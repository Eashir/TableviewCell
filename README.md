### Custom TableviewCell
<br>
    The gist of the stackview setup is shown in the following image along with the UIImages + UILabels.
<br>
    We'll have a total of 9 stackviews!
<br><br>
<img width="575" alt="Screen Shot 2024-01-11 at 10 49 04 AM" src="https://github.com/Eashir/TableviewCell/assets/20934684/7e01358c-5c7f-492f-9fb3-426f949491dc">


<br><br><br><br>

# TableView Setup

Start with the standard viewcontroller. Manually add a tableview to it. Manually add a tableviewcell to the tableview as well. 
Heres what our CustomTableViewController will look like.

**Note** that its a ViewController with tableview methods!

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

// MARK: - UITableViewDelegate + Datasource

extension CustomTableViewController: UITableViewDataSource, UITableViewDelegate {
    
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return 3
    }
    
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        
        let cell = tableView.dequeueReusableCell(withIdentifier: cellIdentifier) as! PersonTableViewCell
        return cell
    }

    
}

```
    CustomTableViewCell setup

```

import Foundation
import UIKit

class PersonTableViewCell: UITableViewCell {
    @IBOutlet weak var ProfileImageView: UIImageView!
    
    override func awakeFromNib() {
        super.awakeFromNib()
    }
    
    override func layoutSubviews()  {
        
        self.ProfileImageView.layer.cornerRadius = self.ProfileImageView.bounds.height/2
        self.ProfileImageView.clipsToBounds = true
    }
    
    override func prepareForReuse() {
        super.prepareForReuse()
    }
    
}

```
<br><br><br><br><br>

You can also set the storyboard cellheight to 150 for now  
*Remember to set the cellreuseidentifier in the storyboard cell we created!*
<br>
<img width="258" alt="Screen Shot 2024-01-12 at 9 22 24 PM" src="https://github.com/Eashir/TableviewCell/assets/20934684/00300256-28ee-4f2d-b9c9-68b7c01a0669">


