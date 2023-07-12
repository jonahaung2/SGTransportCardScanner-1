# SGTransportCardScanner

NFC Transport Card Reader framework for Singapore Transport Cards



    import SwiftUI
    import SGTransportCardScanner
    public class NFCScanner: ObservableObject {
        @Published var cardDetail: NFCCard?
        private let interactor = SGTransportCardScanner()
        public init() {
            interactor.setNfcCardDetectedBlock { [weak self] card in
                guard let self else { return }
                DispatchQueue.main.async {
                    self.cardDetail = card
                }
            }
        }
        public func beginScan() {
            interactor.beginScan()
        }
    }
    