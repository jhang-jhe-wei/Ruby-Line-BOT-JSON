# Ruby-Line-BOT-JSON
- 原連結為 [卡米哥的kamiflex](https://github.com/etrex/kamiflex)
## 在使用前，請完成以下步驟
- 安裝Ruby(不限版本)
- 安裝兩個Gem，於commend Line輸入
```
gem install kamiflex
gem install clipboard
gem install gem "ffi", :platforms => [:mswin, :mingw]            //Windows可能需要?(但我沒用)
```

## 程式碼
- 新增檔案名.rb

```ruby
require "kamiflex"
require "clipboard"
@todos = [
  {
    id: 1,
    name: "ruby",
  },
  {
    id: 2,
    name: "rails",
  },
  {
    id: 3,
    name: "kamiflex",
  },
]

json = Kamiflex.build(self) do
  #從這裡開始改
  bubble do
    body do
      horizontal_box do
        text "🍔", flex: 0, action: message_action("/")
        text "Todos"
        text "🆕", align: "end", action: uri_action("http://www.homiestudio.com.tw/")#這是測試網址哦
      end
      separator
      if @todos
        vertical_box margin: "lg" do
          horizontal_box @todos, margin: "lg" do |todo|
            text todo[:name], action: message_action("/todos/#{todo[:id]}")
            text "❌", align: "end", action: message_action("DELETE /todos/#{todo[:id]}")
          end
        end
      else
        text "no contents yet", margin: "lg"
      end
    end
  end
  #這裡結束
end

puts json
Clipboard.copy(json)

```
### 執行
```
ruby 檔案名.rb
```
