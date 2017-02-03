# Tag-collection-layout

![alt tag](https://github.com/Brusnikin/Tag-collection-layout/blob/master/tags%20collection%20layout.png)

```swift
let titles = ["Freedom", "God", "Happiness", "Imagination", "Intelligence", "Other"]
var buttons = [UIButton]()

func createButton(withTitle title: String) -> UIButton
{
    let button = UIButton(type: .system)
    button.setTitle(title, for: .normal)
    button.titleLabel?.font = UIFont.systemFont(ofSize: 15.0, weight: UIFontWeightRegular)
    button.layer.borderWidth = 0.5
    button.layer.borderColor = UIColor.lightGray.cgColor
    
    let size = button.titleLabel!.text!.size(attributes: [NSFontAttributeName : button.titleLabel!.font!])
    button.frame = CGRect(x: 0.0, y: 0.0, width: size.width + 10.0, height: size.height + 10.0)
    button.titleEdgeInsets = UIEdgeInsetsMake(0.0, 5.0, 0.0, 5.0)
    
    return button
}

for title in titles
{
    buttons.append(createButton(withTitle: title))
}

func createButtonGrid(withButtons buttons: [UIButton]) {
    let offset = 5.0
    var x = 0.0, y = 5.0, row = 0.0
    
    let viewFrame = CGRect(x:0.0, y:0.0, width:200.0, height:200.0)
    let view = UIView(frame: viewFrame)
    view.backgroundColor = UIColor.white
    
    for idx in 0..<buttons.count
    {
        let button = buttons[idx]
        
        row += Double(button.frame.width) + offset
        
        if row < Double(viewFrame.width)
        {
            x = idx == 0 ? offset : row - Double(button.frame.width)
        }
        else
        {
            x = offset
            row = Double(button.frame.width) + offset
            y += Double(button.frame.height) + offset
        }
        
        let frame = CGRect(x:CGFloat(x), y:CGFloat(y), width:button.frame.width, height:button.frame.height)
        button.frame = frame
        
        view.addSubview(button) //quick look
    }
}
createButtonGrid(withButtons: buttons)
```
