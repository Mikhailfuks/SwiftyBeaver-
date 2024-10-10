import UIKit
import SwiftyBeaver

class ViewController: UIViewController {
    let log = SwiftyBeaver.self

    override func viewDidLoad() {
        super.viewDidLoad()

        // Set up logging destinations
        setupLogging()
        
        // Example logging
        log.info("View did load")
    }

    func setupLogging() {
        let console = ConsoleDestination()  // log to Xcode Console
        console.minLevel = .debug // Show all levels of log messages
        log.addDestination(console)

        // Optional: file destination
        let file = FileDestination()  // log to a file
        file.minLevel = .debug // Show all levels of log messages
        log.addDestination(file)
    }

    func performOperation() {
        // Log an operation
        log.debug("Performing some operation")
        
        // Simulate an error
        let success = false
        if !success {
            log.error("There was an error performing the operation")
        }
    }
}

