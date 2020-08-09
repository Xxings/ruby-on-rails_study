

## 공부방향

[docs]()

[Rails Setting](https://rubykr.github.io/rails_guides/getting_started.html)

[한 눈에 읽는 루비 온 레일즈](https://edu.goorm.io/lecture/16335/%ED%95%9C-%EB%88%88%EC%97%90-%EC%9D%BD%EB%8A%94-%EB%A3%A8%EB%B9%84-%EC%98%A8-%EB%A0%88%EC%9D%BC%EC%A6%88)

[생활코딩 - Router](https://opentutorials.org/course/2835/19602)

### Sample

[heroku](https://frozen-spire-16874.herokuapp.com/)

프로젝트 하나 Clone 시작







## 환경

Rails 5.2.4.3

```bash
sudo gem install rails -v 5.2.4.3
```

```
gem install rubocop
```





[LiveReload extension](https://chrome.google.com/webstore/detail/livereload/jnihajbhpnppcggbcgedagnkighmdlei) ( 프론트 수정사항 반영 )

```ruby
#import Gemfile
group :development do  gem 'guard'  gem 'guard-livereload', '~> 2.5'  gem 'rack-livereload', '~> 0.3.16'end
```

```bash
bundle installguard init livereload
```

```ruby
#import config/environments/development.rb
config.middleware.insert_after ActionDispatch::Static, Rack::LiveReload, host: 'Second URL', port: 80

```

```ruby
#import Guardfile
guard 'livereload', port: {Port} do
```

```bash
guard
#INFO-LiveReload is waiting for a browser to connect 확인
```

또는,

[Preview on Web Server](https://marketplace.visualstudio.com/items?itemName=yuichinukiyama.vscode-preview-server)

- `Preview on side panel (ctrl+shift+v)`: Open preview of HTML on side panel. With this feature, you can easely check the operation of HTML, CSS and JavaScript.
- `Launch on browser (ctrl+shift+l)`: Open Web Page on default browser. You can check all operation with web page.
- `Stop the web server (ctrl+shift+s)`: Stop the web server. This feature can be used only from command palette.
- `Resume the web server (ctrl+shift+r)`: Resume the web server. This feature can be used only from command palette.
- `show UI Page (ctrl+shift+u)`: Show UI Page. You can change options at UI page.



## Rails 폴더 구성

```t
/myapp

	/app : 애클리케이션의 메인 폴더.
		/assets : 어셋(자바스크립트, 스타일시트, 그림 등의 리소스)
		/images
		/javascripts
		/stylesheets

	/controllers : 컨트롤 클래스
		/concerns : 컨트롤 공통 모듈
		application_controller.rb : 애플리케이션 공통 컨트롤러

	/helpers : 뷰 헬퍼
		application_helper.rb : 애플리케이션 공통 뷰 헬퍼

	/mailers : 액션 메일러 구현 클래스

	/models : 모델 클래스
		/concerns

	/views : 뷰 스크립트
		/layouts : 레이아웃
		application.html.erb : 애플리케이션 공통 레이아웃

	/bin : 코드 생성 또는 개발 서버 실행에 사용되는 헬퍼 스크립트

	/config : 애플리케이션 자체와 라우팅 등의 설정
		/environments : 환경 단위의 설정파일
		/initializers : 초기화 파일
		/locales : 국제화 대응을 위한 리소스 파일

	/db : 데이터베이스 자체 또는 스키마 정보. 마이그레이션 파일 등

	/lib : 사용자 정의 라이브러리 등

	/log : 로그 출력 위치

	/public : 공개 폴더

	/test : 테스트 스크립트 등

	/tmp : 임시 파일

	/vendor : 서버 파티 코드

	config.ru : 애플리케이션 엔트리 포인트

	Gemfile : 필요한 gem 파일 정의

	Rakefile : 터미널로부터 사용가능한 작업

	README.rdoc : readme
```





## Rails 특징

1. **Convention over Configuration(설정보다 규칙)** (CoC)
   : Rails는 개발자가 설정해야 할 요소를 최대한 줄이고, 이를 규칙으로 미리 제공하여 빠른 개발을 가능하게 합니다. 기능을 개발할 때 한 가지 최선의 모범 답안을 가정하면, Rails는 그 답안을 실행하기 위해 필요한 기본 설정을 미리 제공하는 것이죠. 그러니 **Rails에서 미리 제공하는 규칙**을 지키며 개발한다면, **개발자는 정말 필요한 개발 작업에만 집중**할 수 있어 웹 서비스를 굉장히 빠르게 구현할 수 있습니다. 물론 단점 또한 명백하게 존재합니다. 초기에 Rails를 커스터마이징 하려면 Rails의 규칙에 대해 이해해야 하기 때문에 직접 처음부터 모든 것을 개발하며 사용 방식을 체득하는 다른 프레임워크에 비해 초기 진입 장벽이 높다고 느낄 수 있습니다.

   

2. **Don't Repeat Yourself (DRY)**
   : 같은 코드를 반복하지 마세요! Rails는 사용자가 코드 작성 또는 설정 세팅을 반복하지 않도록 **다양한 자동화 옵션을 제공**합니다. 예를 들어, 다른 프레임워크에서는 사용자가 직접 데이터베이스 스키마를 정의해야 했지만 Rails에서는 그럴 필요가 없습니다. 데이터베이스 테이블을 만들면 Rails가 자동으로 스키마 설정을 진행합니다.

   

3. **MVC 패턴**
   : MVC 패턴은 Rails가 채택한 디자인 패턴으로, 이는 **Model, View, Controller**의 약자입니다. MVC 패턴은 하나의 어플리케이션 또는 프로젝트를 구성할 때, 그 구성요소를 3가지 역할로 구분한 패턴입니다.

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ghklg0oeq6j30va0u0gxv.jpg" alt="image-20200809163128757" style="zoom:50%;" />

### 디렉토리 구조

1. **app/controllers**
   : app 디렉토리의 하위 디렉토리인 controllers 안에 생성되는 파일은 Rails의 MVC 패턴에서 controller에 해당하는 코드가 담겨있습니다.

   

2. **app/views**
   : app 디렉토리의 하위 디렉토리인 views에는 MVC 패턴에서 view에 해당하는 코드가 들어갑니다. Rails에서 view는 controller 내부의 action과 일대일 매칭되어 설정됩니다. 자세한 내용은 후속 강의에서 다루겠습니다.

   

3. **app/models**
   : app 디렉토리의 하위 디렉토리인 models는 Rails MVC 패턴에서 model 역할을 수행합니다. 내부적으로 설정된 데이터베이스와 연동되어서 관련 테이블을 class화 시킨 것이 model이라고 생각하시면 됩니다.

   

4. **config/routes.rb**
   : config 디렉토리에 포함되어 있는 routes.rb 파일은 클라이언트에서 요청하는 URL을 특정 controller의 action과 매칭시킵니다.

   

5. **db/migrate**
   : 사용자가 model을 사용하려면 Rails 프로젝트와 연결된 데이터베이스에 실제로 테이블을 생성해야 합니다. 실제 테이블을 만들기 위한 코드들은 db 디렉토리의 하위 디렉토리인 migrate에 파일 형태로생성됩니다.

   

6. **db/schema.rb**
   : 실제로 데이터베이스에 테이블이 생성되면 Rails 프로젝트의 db 디렉토리 하위에 생성되는 파일입니다. 이 파일에서 데이터베이스 테이블의 스키마를 확인할 수 있습니다.

   

7. **vendor/Gemfile**
   : Ruby에서 라이브러리를 Gem이라고 부릅니다. Rails 프로젝트에서는 여러 Gem을 추가하며 개발을 진행하는데, Gem은 vendor 디렉토리 하위에 포함된 Gemfile에 작성하여 Rails 프로젝트에 추가할 수 있습니다.



### 컨트롤러

```bash
rails g controller 
```



### 모델

```bash
rails g model
```

1. `db/migrate/xxxx_crate_posts.rb` 파일은 데이터베이스 테이블 필드 등의 정보를 정의할 수 있는 마이그레이션 파일입니다.

   ```bash
   #migrate로 테이블 생성
   rake db:migrate
   ```

2. `app/model/post.rb`는 Rails에서 사용할 model 입니다. 1번 마이그레이션을 통해 생성된 posts 테이블과 연결하여 사용합니다.

   ```bash
   #CRUD
   rails g controller posts index new edit create show update destroy 
   ```

   ```ruby
   class PostsController < ApplicationController
     def index
       #SELECT * FROM POST
       @posts = Post.all
     end
   
     def new
      
     end
   
   
     def edit
       @post = Post.find(params[:id])
     end
   
     #C
     def create
       Post.create(title: params[:title], content: params[:content])
       redirect_to "/posts/index"
     end
     #R
     def show
       @post = Post.find(params[:id])
     end
     #U
     def update
       @post = Post.find(params[:id])
       @post.update(title: params[:title], content: params[:content])
       redirect_to "/posts/show/#{@post.id}"
     end
     #D
     def destroy
       @post = Post.find(params[:id])
       @post.destroy
       redirect_to "/posts/index"
     end
   end
   
   ```
   
   

그 다음 파일부터는 그 이름 규칙이 복잡합니다. Rails의 특징인 '설정보다 규약' 때문입니다. 레일즈에서 설정해둔 규칙이니 알고 넘어가는 것이 좋습니다.

1. 모델 클래스의 규칙은 단수형의 CamelCase입니다. 첫 글자는 대문자로, 띄어쓰기는 생략하고 그 다음에 오는 문자는 대문자로 설정해야 합니다.
   (ex) `Post`, `PostComment`
2. 모델 클래스의 파일 이름은 단수형의 snake__case 를 사용합니다. 첫 글자는 소문자로, 띄어쓰기 대신 '_'를 사용합니다.
   (ex) `post.rb`, `post_comment.rb`
3. 테이블은 복수형의 snake_case입니다. 복수형이라해서 단순하게 모든 단수형에 s만 붙이지 않습니다. Person이라는 모델을 만들면 table명은 people로 변환되는 등 몇 가지 재밌는 처리가 있죠.
   (ex) `posts`, `post_comments`

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ghkobreg11j30rw0nwn0h.jpg" alt="image-20200809181114275" style="zoom:25%;" />

### Scaffold

1. 빠르게 동작하는 프로젝트
2. 일반적인 CRUD 크게 벗어나지 않을때

```
rails g scaffold Post title:string content:text
```

1. active_record
   : scaffold로 인해 생성한 Post 모델에 관한 부분

2. resource_route
   

***제약조건**

   1. **리소스는 동사를 사용하지 않고 명사로 작성**한다는 점입니다. 리소스는 행위를 표현하지 않고 행위의 주체, 즉 자원만 표현합니다. 때문에 행위(동사) 부분은 HTTP 메서드로 대신합니다.
   
   2. **리소스는 콜렉션과 도큐먼트(멤버)로 이루어진다**는 점입니다. 도큐먼트는 문서 또는 한 객체로, 콜렉션은 도큐먼트의 집합 또는 객체들의 집합이라고 생각하시면 됩니다. 때문에 콜렉션을 표현할 땐 복수형으로, 도큐먼트를 표현할 땐 단수형 또는 콜렉션 뒤에 id 값을 입력하여 표현합니다.
   
3. scaffold_controller
   **scaffold controller 파일**

   ```ruby
   #  'set_post' before action([:show, :edit, :update, :destroy])
   before_action :set_post, only: [:show, :edit, :update, :destroy]
   # after_action :set_post
   # only: [x,y,z] :: x,y,z만 
   # except: [x,y,z]  :: x,y,z 이외에 
   ```

   

view와 연결되어 있지 않은 일반 메서드를 만들고 싶다면 앞 위치에 **private** 와 **protected**

**respond_to**

format.html / format.json



**Strong parameter**

 `params.require(:post).permit(:title, :content)`

.require(필터링 모델)

.permit(허용 컬럼 리스트)





4. erb
   : 생성되는 뷰 파일들

   **render**

   ​	Partial 지원 ( Rails의 DRY  :: `Don't Repeat Yourself `)

   ​	Partial을 만들때는 _파일명

   **link_to**

   ​	a tag의 뷰 헬퍼

   > Route 헬퍼 확인 [guides ruby on rails](https://guides.rubyonrails.org/routing.html)
	
	1. rake routes
	2. {ip_addr}:{port}/rails/info/routes

   

   **form_with**


   		form의 뷰 헬퍼

5. jbuilder
   : html 형태가 아닌 json 형태로 출력하기 위한 부분

6. assets
   : scaffold에 필요한 scss나 script 요소들



### GEM

[The Ruby ToolBox](https://www.ruby-toolbox.com)

[Awesom Ruby](https://awesome-ruby.com)

maven, Gradle, package-json과 비슷하게 gemfile에 추가



### Usage

* 사용자 인증기능 (devise)

  import gemfile ( 4.7.2 )

  `gem install 'devise'`

```bash
bundle install
# bundle info devise
rails generate devise:install
```

```
rails g devise user
rake db:migrate
```



##  배포

1. **development [개발 환경]**

2. - 개발 환경에서 사용됩니다. 
   - 특정 페이지에서 오류가 생길 시 오류 내용을 브라우저 화면에 띄웁니다.
   - 서버 대부분의 결과를 콘솔 및 로그로 출력하기 때문에 속도가 상대적으로 느립니다.

3. **test [테스트 환경]**

4. - 테스트 환경에서 사용됩니다.

5. **production [운영 환경]**

6. - 배포 시 운영 환경에서 사용됩니다.
   - 오류가 생기면 오류의 내용을 표시하지 않고 404 페이지를 출력합니다.
   - production은 운영 환경이니 불필요한 내부 처리를 하지 않아 속도가 상대적으로 빠릅니다.

### Heroku 배포

> Heroku-cli 설치

 ```bash
brew tap heroku/brew && brew install heroku
heroku login
 ```

> import Gemfile [ sqlite3 -> postgresql ]

```bash
#변경 전
gem 'sqlite3'

#변경 후
gem 'sqlite3', :group => :development
gem 'pg', :group => :production  #postgresql
gem 'rails_12factor', :group => :production
```

> bundle install

```bash
# brew install postgresql
# postgres -V
bundle install
```

> Database (sqlite3 -> postgresql)

```
production:
  <<: *default
  adapter: postgresql
  encoding: unicode
```

```bash
heroku create
git add .
git commit -m "set deploy"
git push heroku master
# db 설정 'We're sorry, but something went wrong.'
heroku run rake db:migrate
```

### Route

**resources**

![image-20200809224646026](https://tva1.sinaimg.cn/large/007S8ZIlgy1ghkwagoxnuj31we0p8k6m.jpg)

* prefix를 앞에 추가할때

  ```ruby
  scope 'admin', as:'admin' do
    resources:photos, :acoounts
  end
  ```

* 이중 resources 구조를 만들때

```ruby
resources:magazines do
  resources:ads, as:'periodical_ads'
end
```

* 파라미터를 :id에서 바꿀때

  ```ruby
  resources:videos, param::identifier
  ```

  

**route & path**

prefix | Verb | URI Pattern

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1ghkwlfhu6oj30c908umxu.jpg" alt="image-20200809225719225" style="zoom: 50%;" />

```ruby
#update
<%= link_to 'Edit', edit_post_path(post) %>
<%= link_to 'Edit', '/post/:id/edit' %>

#Delete
<%= link_to 'Destroy', post, method: :delete, data: { confirm: 'Are you sure?' } %>

```



### REST

* 클라이언트/서버 구조
* 무상태(Stateless)
* 캐시 처리 가능
* 계층화
* Code on demand
* 인터페이스 일관성



### Error

> InvalidAuthenticityToken

POST, PUT, DELETE : HTTP method로 Request시 난수토큰 전달 안했을때 문제

<input name="authenticity_token" value="<%= form_authenticity_token %>" type="hidden">



