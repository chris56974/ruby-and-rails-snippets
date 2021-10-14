# Ruby and Rails Snippets for Visual Studio Code (Vim/Intellisense Bias)

<!-- markdownlint-disable MD033 -->
<p>
  <a href="https://marketplace.visualstudio.com/items?itemName=Cjay.ruby-and-rails-snippets">
    <img src="https://vsmarketplacebadge.apphb.com/version/Cjay.ruby-and-rails-snippets.svg">
  </a>
  <a href="https://marketplace.visualstudio.com/items?itemName=Cjay.ruby-and-rails-snippets">
    <img src="https://vsmarketplacebadge.apphb.com/installs/Cjay.ruby-and-rails-snippets.svg">
  </a>
  <a href="https://marketplace.visualstudio.com/items?itemName=Cjay.ruby-and-rails-snippets">
    <img src="https://vsmarketplacebadge.apphb.com/downloads-short/Cjay.ruby-and-rails-snippets.svg">
  </a>
</p>

[This extension](https://github.com/Chris56974/ruby-and-rails-snippets) (which can also be found on the [marketplace](https://marketplace.visualstudio.com/items?itemName=Cjay.ruby-and-rails-snippets)) is very similar to [Vense's rails extension](https://marketplace.visualstudio.com/items?itemName=Vense.rails-snippets) and [Peng Lv's snippets](https://marketplace.visualstudio.com/items?itemName=rebornix.Ruby) but with my own twists and added snippets.

By default, intellisense does NOT work inside of code snippets (because intellisense and snippets both use the TAB key). If you want to mess around with your settings and enable it anyway you can check out [this stackoverflow post](https://stackoverflow.com/questions/55683145). I prefer having more intellisense, so a lot of these snippets will end earlier than you would expect. I also like to use the vim extension in vscode, so these snippets are biased towards vim users (I use j/k/o/O to move around). If this is not to your liking, I recommend using the previous two extensions instead. You're also free to fork/mess around with this extension as you wish (MIT Licensed).

<a href="https://imgflip.com/gif/34pykn"><img src="https://i.imgflip.com/34pykn.gif" title="made at imgflip.com"/></a>

## Supported File Types

- Ruby (.rb)
- Embedded Ruby (.erb)

### Help

1. You use each snippet by typing out its name (i.e. "ifelse") and then hitting TAB on the keyboard.
2. You must be in one of the supported file types for these snippets to work.
3. Some snippets have multiple steps that you can cycle through.

- Hitting TAB will move you forward one step
- Hitting CTRL + TAB will move you back one step
- You can view suggested snippets by hitting CTRL/COMMAND + SPACE

`$1` is where the snippet starts and `$0` is where the snippet ends

## Ruby snippets

```ruby
# frozen_string_literal_true # fr

map { |$0|   }      # map
map { |$1| $0 }     # mapp
each { |$0| }       # each
each { |$1| $0 }    # eachh
select { |$0| }     # select
select { |$1| $0 }  # selectt

inject($1) { |$0| } # injent
inject { |$0| }     # injectt
all? { |$0| }       # all
all? { |$1| $0 }    # alll
any? { |$0| }       # any
any? { |$1| $0 }    # anyy

for $1 in $0 do # for
end

for $1 in $2 do # forr
  $0
end

loop do # loop (infinite)
  $0
end

# same pattern for while/until/module/unless
while $0 # while
end

while $1 # whilee
  $0
end

do # do
  $0 
end

if $0 # if
end

if $0 # ifelse.. 
else
end

def $0 # def
end

begin # begin
  $0
rescue => 
end

class $1 # cla
  $0
end

def initialize($0) # init
end

# cla1, cla2, cla3...
class $1
  def initialize($2)
    @$2 = $2
  end
  $0
end

# clex
class $1 < $0
end
```

## Rails Snippets .rb

```ruby
only: %i[${1:method}]   # only
except: %i[${1:method}] # except

# Active Record
find_by(${1:key}: ${2:value})              # find_by
find_by(${1:id_name}: params[:${2:param}]) # find_by_params
where($0)

# Routing
get '/${1:route}', to: '${2:controller}#${3:method}'    # get
post '/${1:route}', to: '${2:controller}#${3:method}'   # post
patch '/${1:route}', to: '${2:controller}#${3:method}'  # patch
put '/${1:route}', to: '${2:controller}#${3:method}'    # put
delete '/${1:route}', to: '${2:controller}#${3:method}' # delete

resources :${res_name}              # res
resources :${1:res_name} do $2 end  # resb
resources :${1:res_name} do         # rescb
  collection do
    $2
  end
end

resources :${1:res_name} do # resmember
  member do
    $2
  end
end

resource :${1:res_name} do
  member do
    $2
  end
end

member do
  $1
end

collection do # collection
  $1
end

# Redirects
render $0
redirect_to ${1:path}
redirect_to ${path}, notice: '${msg}' # redirect_to with msg

# Model
has_one :$0
dependent: :${1:id} # dep
has_one :${1:id}, dependent: :${2:type} # has_one_dep
has_many :$0 # has_many
has_many :${1:model1}, through: :${2:model2} # has_many_through 
has_many :${1:id}, dependent: :${2:type}     # has_many_dependent
belongs_to : # belongs_to
belongs_to :${1:id}, cache: ${2:true}  # belongs_to_cache
has_and_belongs_to_many :${1:id}       # has_and_belongs_to_many

## Colunms
add_column :${1:table}, :${2:column}, :${3:type} # add
add_reference :${1:table}, :${2:column}, foreign_key: true # add_reference

## Params/Require
params.require(:${1:id_name}).permit(:${2:variable})
params['$1']['$2']['$3']$0
require '$1'$0
require(:$1)$0
include($1)$0
permit(${1:id});

## Controller
class ${1:Name}Controller < ApplicationController
  $2
end

def index 
  $1
end 

def create 
  $0
end 

def new 
  $0
end 

def edit 
  $0
end 

def show 
  $0
end 

def update 
  $0
end 

def destroy 
  $0
end 

# crud
def index
end 
def new  
end
def create
end
def edit
end
def update
end
def show
end
def destroy
end

before_action :${1:id}
```

## Ruby Templates .erb

```jsx
<% $1 %>  // pre
<%= $1 %> // pe

<% $1 %>  // preb
  $0
<% end %>

<%= $1 %> // peb
  $0
<% end %>

<% ${1:items}.each do |${2:item}| %>
  $0
<% end %>

<%= form_for ${1:variable} do |${2:f}| %>
  $0
<% end %>

<%= f.time_zone_select :${1:id_name} %>
<%= range_field (:${1:model_name}, :${2:id_name}, in: ${3:1..100}) %>
<%= select_tag (:${1:id_name}, options_for_select(${2:options}))%>
<%= color_field :${$1:id_name} %>

options_for_select([${1:options}])$0 

<%= render ${1:path} %>$0 
<%= render ${1:path}, ${2:var1}: ${3:var2} %>
<%= link_to '${1:text}', ${2:path} %>
<%= link_to '${1:text}', ${2:path}, class:'${3:class}' %>
<%= link_to '${1:link_text}', ${2:path}, method: '${3:method}', data:{ ${4:data} } %>
<%= link_to '${1:link_text}', ${2:path}, method: '${3:method}', data:{ ${4:data} }, class:'${5:class}' %>
<%= link_to \"${1:link_text}\", ${2:path}, method: \"${3:method}\", data:{ confirm: \"${4:confirm}\"} %>
<%= link_to \"${1:link_text}\", ${2:path}, method: \"${3:method}\", data:{ confirm: \"${4:confirm}\"}, class:\"${5:class}\" %>
<%= f.submit %>$0
<%= f.label :${1:id_name}, '${2:text}' %>$0
<%= f.number_field (:${1:id_name}, in: ${2:1.0..20.0}, step: ${3:0.5}) %>$0
<%= f.time_field :${1:id_name} %>
<%= f.hidden_field :${1:id_name} %>
<%= f.hidden_field :${1:id_name} %>
<%= f.url_field :${id_name} %>
<%= f.password_field :${id_name} %>
<%= f.text_area :${id_name} %>
<%= f.check_box :${id_name} %>
<%= f.text_field :${id_name} %>
<%= f.date_field :${id_name} %>
<%= f.datetime_field :${1:id_name} %>
<%= f.radio_button :${1:name}, :value => '${2:value}' %>
<%= f.input :${1:id}, label: '${2:text}' %>
${1:path}_path
new_${1:path}_path
edit_${1:path}_path(${2:variable})

<% if $1 %>
  $2
<% end %>

<% else %>
<% elsif $1 %>$0

<% if $1 %>
  $2
<% else %>
  $3
<% end %>

<% if $1 %>
  $2
<% elseif %>
  $3
<% end %>

<% if $1 %>
  $2
<% elseif %>
  $3
<% else %>
  $4
<% end %>

<% unless ${1:falsevalue} %>
  $2
<% end %>

<% unless ${1:falsevalue} %>
  $2
<% else %>
  $3
<% end %>

<% end %>
```

## [MIT License](https://github.com/Chris56974/ruby-and-rails-snippets/blob/master/LICENSE)
