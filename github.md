# GITHUB

## Những gì cần biết khi làm việc với Git trong dự án

### Giới thiệu về Git

Git thì chắc không phải nói nhiều các bạn cũng biết về nó rồi đúng không. Bài này mình không nói nhiều mà các bạn chỉ cần Google là ra cả đống giới thiệu về Git. Mình chỉ nói tóm tắt ngắn gọn cho các bạn mới dùng Git hoặc mới tìm hiểu về Git được biết nó là gì và tại sao cần dùng nó?

Git gần đây nổi lên phổ biến nhất trong số các hệ thống quản lý mã nguồn hoàn toàn mở và miễn phí trên thị trường và nó gần như thay thế hoàn toàn và tuyệt đối ưu thế. Chỉ còn một số dự án cũ vẫn dùng SVN để quản lý tài liệu mà thôi còn lại dần dần họ cũng migrate hết lên Git. Ngay cả cha đẻ của TFS là Microsoft cũng hỗ trợ Git một hệ quản trị mã nguồn (SCM – Source Control Management) song song với TFS trên Azure DevOps. Các bạn cũng thấy có một platform là Github đang thống trị thị trường chia sẻ code với một lượng developer và repository khổng lồ.

Vậy Git là gì? Nó là hệ thống quản lý mã nguồn phi tập trung và nó được phát triển bởi chính cha đẻ của Linux là Linux Torvald. Cái hay của nó chính là ở sự phi tập trung mà mình làm việc nhiều mới thấy nó hay. Ví dụ trước đây chúng ta làm việc với Visual Source Safe, SVN, TFS…thì đều là quản lý ở dạng tập trung tức là làm xong phải đẩy code lên server để tracking, server quản lý toàn bộ nhánh code và nếu server chết thì cũng chết luôn không commit gì được?

Còn phi tập trung hay cái là chúng a cứ thao tác bình thường trên mỗi máy local, bao gồm các thao tác thường thấy như commit, merge, rebase… Và chỉ khi nào cần push code chia sẻ cho các member khác trong team mới cần Git server.

Một tình huống nữa là nếu lỡ không may code trên Git server bị mất thì bất cứ máy nào có nhánh code đó đều có thể push lên được, rất tiện và an toàn phải không nào?&#x20;

Giờ có 1 điểm quan trọng là chúng ta phải hiểu được Git nó có những trạng thái nào khi làm việc thì chúng ta mới hiểu được nó:

&#x20;

<img src="https://tedu.com.vn/uploaded/images/012021/gitflow.png" alt="" data-size="original">

Đây là sơ đồ trạng thái của file từ khi tạo ra đến khi chúng ta đẩy lên Git, cơ bản thì nó có 3 trạng thái dưới local và 1 trạng thái đẩy lên server hay chưa (qua câu lệnh git push). Về cơ bản chúng ta chỉ cần nhớ git có 3 trạng thái thay vì 2 trạng thái như cac thằng khác.

1\. Workspace: tức là file tạo ra chưa add vào git change, sau lệnh git add thì mới add vào staging

2\. Staging là các thay đổi được chuẩn bị để commit

3\. Trạng thái đã commit vào local repository

Trạng thái sau cùng là được push lên server hay chưa, cái này thì tùy nếu bạn đã add repository vào local repository thì mới cần còn không thì làm việc nguyên dưới local là đủ. Nhìn vào hình trên ta cũng thấy mỗi giai đoạn cần dùng lệnh gì trực quan phải không nào?

Giờ chúng ta sẽ tìm hiểu một số từ khóa cần biết trong Git nhé.

### Các từ khóa cần biết trong Git

**Git**: Tên hệ thống quản trị mã nguồn (nó tương đương SVN hay TFS…) và nó không phải Github nhé.

**Github**: Là một dịch vụ lưu trữ và chia sẻ mã nguồn sử dụng hệ thống quản trị Git, ngoài ra có Azure DevOps, Bitbucket…

**Repositories**: Là nơi đặt mã nguồn git, thường là 1 project sẽ tạo 1 Repository riêng hoặc 1 Repository chứa nhiều mã nguồn nhiều project con. Nói chung nó là một bộ mã nguồn nếu muốn lưu trữ trên git thì chúng ta đều phải tạo ra 1 repository và đẩy code lên đó. Thường thì 1 account Git hoặc 1 project sẽ cho tạo nhiều Repository trên đó. Ví dụ: [https://github.com/](https://github.com/teduinternational)vuluu2k đây là Github account của mình chứa nhiều Repository trên đó, mỗi repository là một mã nguồn.

**Branch**: Mỗi một repository chúng ta chia ra nhiều nhánh code, để giúp các developer hay nhóm phát triển các tính năng độc lập của phần mềm mà không bị ảnh hưởng đến nhau, mỗi nhánh sẽ là một danh sách các commit mà không ảnh hưởng đến danh sách commit của nhánh khác, chúng được sắp xếp theo thời gian trước sau. Chỉ khi merge nhánh này với nhánh kia thì code mới được nhập chung với nhau.

**Commit**: Mỗi lần chúng ta làm xong chúng ta muốn báo cho Git lưu lại các thay đổi so với code nguyên bản trước khi sửa thì chúng ta cần lưu lại các thay đổi trong commit. Một commit là một lần chúng ta lưu lại code vào Git nó sẽ tự sinh ra 1 commit Id, chúng ta có thể quay về bất cứ commit nào trong lịch sử sửa code. Hoặc là tra xem sự khác nhau giữa các commit ra sao?

**Merge code**: Là hành động merge code giữa 2 nhánh code từ một nhánh A vào 1 nhánh B hoặc ngược lại, nhánh được merge sẽ chứa code của cả 2 nhánh và tạo ra một commit mới là merged commit.

**Rebase code**: Cũng là một hành động merge code nhưng không tạo ra commit mới là merged commit mà sắp xếp các commit theo thứ tự thời gian của cả 2 nhánh, history sẽ đẹp tuy nhiên 2 nhánh mà lâu không rebase sẽ phải so sánh theo thời gian từng commit một sẽ mất thời gian.

**Conflict**: Là sự xung đột khi merge code hay rebase khi mà cả 2 thành viên cùng sửa một đoạn code ở cả 2 nhánh lúc merge vào sẽ xung đột và Git hỏi xem muốn lấy sự thay đổi nào hoặc lấy cả 2.

**Stash**: Là tính năng lưu tạm các sự thay đổi vào local khi chúng ta đang làm code dở ở nhánh A nhưng lại chưa muốn commit thì chúng ta phải sang nhánh B để fix bug nên chúng ta phải stash lại để không bị mất code cũng không phải commit. Khi quay lại nhánh A sẽ apply stash để sửa tiếp.

**Gitignore**: Là file nằm trong repository chúng ta tạo ra với tên. gitignore nằm liệt kê các file hay folder nằm trong folder git mà chúng ta không muốn git tracking mà chỉ lưu ở local thôi. Nó sẽ không đánh dấu sự thay đổi khi có thay đổi trong cac file này.

### Cài đặt Git trên máy Windows

Trên Windows hay Mac các bạn cứ vào đây download rồi cài trên máy: [https://git-scm.com/](https://git-scm.com/) cài xong bật CMD Prompt chạy thử lệnh git nếu không lỗi là ok.

### Các tính năng của Git cần thiết cho dự án mà bạn cần biết

Có rất nhiều lệnh trong Git nhưng trong quá trình mình làm việc thì mình chỉ cần sử dụng 15 lệnh như sau để làm việc với Git. Nên các bạn cũng không cần nhớ nhiều quá mà chỉ cần nhớ các lệnh bên dưới để làm việc tốt với Git.

#### Lệnh git init

Lệnh này dùng để khởi tạo một Repository trên máy local, tuy nhiên nó chưa được push lên server mà chúng ta vẫn có thể thao tác với tất cả các lệnh như bình thường và nó hoạt động như một repository thực thụ trừ share code cho các thành viên khác.

```
git init
```

Để init một repository thì chỉ cần vào một folder trống mở Command Prompt rồi gõ lệnh git init nếu thành công thì thư mục đó sẽ thành một Git repository các bạn có thể show hidden file and folders sẽ thấy thư mục tên là. git ẩn.

#### Lệnh git clone

Cách 2 để tạo một git repository là lệnh clone, lệnh này sẽ lấy code từ một Git service trên mạng được public và download về máy sau đó tự tạo luôn một Git repository local kết nối với git remote luôn. Ví dụ chúng ta cần download code của repository có tên eShopSolution về máy chúng ta cần chạy:

```
git clone https://github.com/teduinternational/eShopSolution.git
```

#### &#x20;Lệnh git pull

Lệnh git pull dùng để cập nhật code mới từ trên remote server và nó cũng tự động merge code từ nhánh tương ứng trên server về, ví dụ chúng ta có nhánh develop trên server nó sẽ là tên của origin remote (origin/develop) nếu có ai commit và push code lên nhánh đó khi pull về nó sẽ tự merge code của họ ở nhánh đó vào nhánh develop trên máy chúng ta. Nhánh local trên máy và nhánh origin/develop liên kết với nhau qua cơ chế set upstream. Cú pháp là git pull origin hoặc git pull đều được. Nếu git pull thì mặc định nó sẽ lấy từ nhánh hiện tại còn chỉ ra nhánh sẽ pull từ nhánh đó. Thông thường chỉ cần switch sang nhánh cần pull bằng lệnh git checkout rồi gọi git pull. Trong trường hợp chúng ta có 1 remote repository thì chỉ cần git pull là đủ. Trừ khi có 2 repo thì chỉ ra tên remote repository

```
git pull
```

&#x20;

#### Lệnh git add

Lệnh git add nhằm add các file mới được tạo vào git tracking (stage), một file mới tạo ra sẽ ở chế độ unstage, khi chúng ta add vào stage thì mới commit được vào Git repository.

Để add toàn bộ sự thay đổi chúng ta dùng&#x20;

```
git add *
```

Nếu không sẽ cần chỉ ra tên của file cần add thay vì dấu \*&#x20;

#### Lệnh git fetch

Git fetch cũng cập nhật thay đổi từ server nhưng không tự merge như git pull mà chỉ đóng vai trò get latest xem có commit nào mới từ server hay không nó tương đương F5 refresh vậy.

```
git fetch
```

&#x20;

#### Lệnh git remote

Lệnh này để thao tác với origin remote của chúng ta, ví dụ chúng ta có repository local nhưng khi muốn đưa code lên server Github chúng ta cần tạo một Repository trên Github và tạo origin trên đó sau đó mới đẩy code lên. Để tạo origin thì phải dùng lệnh này.

Lện dưới dùng để thêm một remote repository vào local repository với tên và url.

```
git remote add <remote_name> <url>
```

Lấy danh sách remote origin&#x20;

```
git remote
```

#### Lệnh git reset

Lệnh này để xóa sự thay đổi của chúng ta về trạng thái ban đầu chưa sửa hoặc về bất cứ commit nào trong quá khứ

Reset về HEAD tức là về commit cuối cùng của nhánh đó:

```
git reset --hard HEAD       (về commit HEAD)
git reset --hard HEAD^      (về commit trước HEAD)
git reset --hard HEAD~1     (về trước 1 commit so với "^")
git reset --hard HEAD~2     (về commit trước 2 commit với HEAD)
```

&#x20;

#### Lệnh git checkout

Lệnh này chuyển nhánh trong Git giữa nhánh nọ nhánh kia

```
git checkout <branch_name>
```

#### Lệnh git commit

Lệnh này commit code changes vào Git với một commit message. Ví dụ: chúng ta commit sự thay đổi với message là "First commit":

```
git commit -m "First commit"
```

#### Lệnh git push

Lệnh này đẩy code đã commit lên remote repository

```
git push <remote_repository_name> <branch_name>
```

#### Lệnh git config

Lệnh này config các loại trong Git repository như user, email, tool merge code, tool editor...

tham khảo tại: [https://www.atlassian.com/git/tutorials/setting-up-a-repository/git-config ](https://www.atlassian.com/git/tutorials/setting-up-a-repository/git-config%C2%A0)

Ví dụ config user hiển thị trong các commit:

```
git config user.email "demo@gmail.com"
```

#### Lệnh git merge

Lệnh này merge code nhánh nọ vào nhánh kia. Ví dụ đang ở nhánh A merge code vào nhánh B.

```
git merge nhanh_b
```

#### Lệnh git stash

Lệnh này tạo stash từ code change hoặc apply stash.

```
git stash save --lưu change hiện tại vào stash
git stash list --hiển thị danh sách stash
git stash apply <stash_name> --đẩy changes từ 1 stash vào một nhánh
```

#### Lệnh git status

Lệnh xem trạng thái của git repository xem đang ở nhánh nào có thay đổi gì không.

```
git status
```

#### Lệnh git branch

Lệnh này giống checkout để chuyển nhánh nhưng lại có thêm tính năng tạo nhánh mới.

```
git branch <branch_name> --tạo nhánh mới
git branch -b <branch_name> --checkout và tạo nhánh mới
```

Ngoài ra chúng ta có các lệnh khác như git log để xem lịch sử commit hay git diff để xem sự khác nhau trước khi commit nhưng thực tế thì ít dùng vì mình toàn xem thay đổi hay lịch sử ở Visual Studio hoặc ở Source Tree. Ít khi gõ lệnh vì xem ở đó trực quan hơn.

### Ví dụ case thực tế

Để dễ hình dung hơn thì mình nêu ra một case thực tế trong dự án khi chúng ta khởi tạo một repository đồng thời commit tạo nhánh các kiểu nhé. Để xem mình sẽ phải chạy những lệnh nào nhé.

```
git init --> Khởi tạo một git repository trên local
git add README.md --> Add một file bất kỳ nên là 1 file README.md để mô tả (sử dụng markdown để ghi)
git commit -m "first commit" --> Commit file đó vào git
git branch -M master --> đổi tên nhánh thành master
git remote add origin https://github.com/teduinternational/test.git --> add một remote repository tên là origin với url là repository trên Github/
git push -u origin master --> Push nhánh master từ local lên nhánh master trên origin.
```

Sau khi có commit đầu tiên chúng ta có thể cần tạo thêm nhánh mới tên là develop để phát triển, nhánh master để nguyên bản đó để khi nào release bản 1.0 mới merge lên master vì master luôn đại diện cho code version đang chạy ở môi trường production.

```
git branch -b develop --> Tạo nhánh develop và thực hiện một số sự thay đổi
git add .gitignore --> Tạo file gitignore để thêm các thành phần muốn bỏ qua
git status --> Kiểm tra xem sự thay đổi có đúng không
git add * --> Thêm file gitignore vào stage area
git commit -m "Add gitignore file"
git push origin develop --> đẩy nhánh develop lên remote repository
git status --> Check tiếp xem có gì thay đổi và nhánh hiện tại là gì
git checkout master --> Chuyển nhánh hiện tại sang master
git fetch origin --> Lấy trạng thái mới nhất xem có ai commit lên master hay không
git pull origin master --> Nếu có thì pull về để lấy code mới nhất
git merge develop --> Merge file gitignore đang đặt ở nhánh develop sang master
git push origin master --> Lại đẩy sự thay đổi ở master dưới local lên master trên server.
```

Cứ như thế là chúng ta làm thử xem sao. Tự tạo tài khoản Github để thực hành nhé.

### Tổng kết

Trên đây là tổng quan các lệnh của Git mà chúng ta cần biết khi làm việc với nó. Các bạn có thể tam khảo danh sách các tính năng của nó ở đây: [https://git-scm.com/docs](https://git-scm.com/docs).&#x20;

Các lệnh này để các bạn hiểu còn thực tế làm dự án khi nào cần dọa ai đó thì mới gõ lệnh còn lại thì IDE nào họ cũng hỗ trợ thao tác với git nên các thao tác chúng ta thường làm trên Editor như VSCode, Visual Studio hay tool UI phổ biến như Source Tree.

Tuy nhiên các bạn cần nên biết để nếu có không quen dùng tool hoặc thao tác nào tool không hỗ trợ thì gõ lệnh cho pro. Với lại ưu điểm thì lệnh chúng ta tua sẽ nhanh vì gõ xong họ lưu history nếu chỉ cần bấm mũi tên là nó hiện lại lệnh chúng ta vừa thực thi.
