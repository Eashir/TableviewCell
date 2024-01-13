# Custom TableviewCell

The gist of the stackview setup is shown in the following image along with the UIImages + UILabels.
&nbsp;

We'll have a total of 10 stackviews!

<img width="575" alt="Screen Shot 2024-01-11 at 10 49 04 AM" src="https://github.com/Eashir/TableviewCell/assets/20934684/7e01358c-5c7f-492f-9fb3-426f949491dc">

```
import UIKit

class CustomTableViewController: UIViewController {  
    @IBOutlet weak var tableView: UITableView!
    var persons: [Person] = []
    var cellIdentifier = "PersonCellReuseIdentifier"    
    override func viewDidLoad() {
        super.viewDidLoad()
        self.tableView.delegate = self
        self.tableView.dataSource = self
    }    
}
extension CustomTableViewController: UITableViewDataSource, UITableViewDelegate {
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return 3
    }
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {    
        let cell = tableView.dequeueReusableCell(withIdentifier: cellIdentifier) as! PersonTableViewCell
        return cell
    } 
    func tableView(_ tableView: UITableView, heightForRowAt indexPath: IndexPath) -> CGFloat {
        return 150
    }   
}
```




