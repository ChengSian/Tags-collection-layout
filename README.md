# Tag-collection-layout

```swift
let titles = ["Freedom", "God", "Happiness", "Imagination", "Intelligence", "Other"]
var buttons = [UIButton]()

func createButton(withTitle title: String) -> UIButton {
    let button = UIButton(type: .System)
    button.setTitle(title, forState: .Normal)
    button.titleLabel?.font = UIFont.systemFontOfSize(15.0, weight: UIFontWeightRegular)
    button.layer.borderWidth = 0.5
    button.layer.borderColor = UIColor.lightGrayColor().CGColor
    button.contentEdgeInsets = UIEdgeInsetsMake(5.0, 15.0, 5.0, 15.0)
    button.sizeToFit()
    return button
}

for title in titles
{
    buttons.append(createButton(withTitle: title))
}

func createButtonGrid(withButtons buttons: [UIButton]) {
    let offset = 5.0
    var x = 0.0, y = 0.0, row = 0.0

    let viewFrame = CGRectMake(0.0, 0.0, 250.0, 200.0)
    let view = UIView(frame: viewFrame)
    view.backgroundColor = UIColor.whiteColor()

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

        let frame = CGRectMake(CGFloat(x), CGFloat(y), button.frame.width, button.frame.height)
        button.frame = frame

        view.addSubview(button) //quick look
    }
}
createButtonGrid(withButtons: buttons)
```
