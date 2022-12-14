# ๐Soso
<br>

[๋ธ์ ๊ฐ๋ฐ์ผ์ง](https://rhetorical-durian-6e6.notion.site/73948f6e42834d25bc398fa3b8495fa6?v=a25123e01c9e4b49bc1fcca129261ec0)

---

### ๐ ํ๋ก์ ํธ ์๊ฐ
- ์์ํ์ง๋ง ํ๋ฒํ์ง ์์ ์ฐ๋ฆฌ๋ค์ ์ผ์์ ๊ณต์ ํ๋ ๊ณต๊ฐ์๋๋ค!

<br>

### ๐ฐ ์ ์๊ธฐ๊ฐ & ํ์ ์๊ฐ
- 2022-09-02 ~ 2022-09-08

- ์ด์ค์ฌ : ํ๋ก ํธ์๋, ๋ฉ์ธํ์ด์ง & ๊ฒ์๊ธ ๊ด๋ จ API ํต์  ๋ฐ view
- ์ดํฌ์ : ํ๋ก ํธ์๋, ์์ธํ์ด์ง & ๋๊ธ, ์ข์์ ๊ด๋ จ APIํต์  ๋ฐ view
- ์ด์ฃผํ : ๋ฐฑ์๋, JWT๋ฅผ ์ ์ฉํ ๋ก๊ทธ์ธ, ํ์๊ฐ์ ๊ธฐ๋ฅ
- ๊น๋ํ : ๋ฐฑ์๋, ๋๊ธ๊ณผ ์ข์์ ๊ธฐ๋ฅ
- ๊ฐ๋ฏผ์น : ๋ฐฑ์๋, ๊ฒ์๊ธ ์กฐํ, ์์ฑ, ์์ , ์ญ์  ๊ธฐ๋ฅ

<br>

### โ ์ฌ์ฉ ๊ธฐ์ 

`Back-end`
-   Java 11
-   Spring Boot 2.7.2
-   H2, MySQL
-   Spring security, JWT
-   AWS S3, IAM, EC2

`Front-end`

-   JavaScript
-   React

<br>

### โย ๊ตฌํ ๊ธฐ๋ฅ

-   ์ ์ฒด ๊ฒ์๊ธ ๋ชฉ๋ก ์กฐํ (์ด๋ฏธ์ง, ์ข์์)
-   ๊ฒ์๊ธ ์์ฑ (์ ๋ชฉ, ์ด๋ฏธ์ง ์๋ก๋)
-   ๊ฒ์๊ธ ์์ธ์กฐํ (์ ๋ชฉ, ์ด๋ฏธ์ง, ๋๊ธ, ์ข์์)
-   ๊ฒ์๊ธ ์์  ๋ฐ ์ญ์  ๊ธฐ๋ฅ

<br>

### ๐ต API

<br>
<img width="520" alt="api 11" src="https://user-images.githubusercontent.com/110277186/189059190-8941e4c3-bdb4-4262-8f57-b96349b78654.png">
<img width="518" alt="api 22" src="https://user-images.githubusercontent.com/110277186/189059197-8feb39eb-47e0-4b70-9a4c-860d7583ecbd.png">
<img width="526" alt="api 3333" src="https://user-images.githubusercontent.com/110277186/189059688-28a271f5-8f35-4726-8577-28070b52728a.png">




<br>

### โย Trouble Shooting

1. ๊ฒ์๊ธ ๋ฑ๋ก์ ์ด๋ฏธ์ง ์๋ก๋ ๋๊ฒ ํ๊ธฐ

	- ๊ฒ์๊ธ์ ๋ฑ๋กํ  ๋ ์ ๋ชฉ์ ์๋ ฅํ๊ณ  ์ด๋ฏธ์ง๋ฅผ ๋ฑ๋กํ  ์ ์๋๋ก ํ๋ ค๊ณ  ํ๋ค.
	- ๋ฌธ์ 1 : POSTMAN์ผ๋ก API ํ์คํธ๋ฅผ ํ  ๋,  ์ ๋ชฉ์ content-type์ด json์ด๊ณ  ์ด๋ฏธ์ง๋ multipartFile์ด๊ธฐ ๋๋ฌธ์ ๊ธฐ์กด body์ raw๋ฐ์ดํฐ๋ฅผ json์ผ๋ก ์๋ ฅํ๋ ๊ฒ์ ๋ถ๊ฐ๋ฅํ๋ค.
		- ๊ตฌ๊ธ๋งํ ๊ฒฐ๊ณผ PostMapping ์ด๋ธํ์ด์์ 'consumes' ๋ผ๋ ์์๋ก type 2๊ฐ์ง๋ฅผ ๋ช์ํด์ฃผ๊ณ , ํ๋ผ๋ฏธํฐ๋ @RequestPart๋ผ๋ ๊ฒ์ ์ฌ์ฉํ์๋ค.
		```java
		// ๊ฒ์๊ธ ๋ฑ๋ก  
		@PostMapping(value = "/api/auth/post", consumes = {MediaType.APPLICATION_JSON_VALUE, MediaType.MULTIPART_FORM_DATA_VALUE})  
		public PostResponseDto createPost(@RequestPart PostRequestDto postRequestDto, @RequestPart(required = false) MultipartFile multipartFile) throws IOException {  
		  
		    return postService.createPost(postRequestDto, multipartFile);  
		  
		}
		``` 
		- APIํ์คํธ ํ  ๋๋ ์๋์ ๊ฐ์ด form-data๋ก content-type๋ฅผ ๋๋ ์ ๋ณด๋ธ๋ค.
		![apiํ์คํธ](https://user-images.githubusercontent.com/93110733/188308424-3f28dfa3-0f03-4204-b9fb-a99ca929f3a7.JPG)

	- ๋ฌธ์ 2 : entity์์ imgUrl์ nullable=true๋ก ์ค์ ํ์๋๋ฐ๋ ์ด๋ฏธ์ง๊ฐ ์๋ก๋ ๋์ง ์์ผ๋ฉด ํ์ผ์ ๋ณํํ  ์ ์๋ค๋ ์ค๋ฅ๊ฐ ์๊ฒผ๋ค. 
		- multipartFile์ด null์ด์ด๋ S3Uploader์์ ํ์ผ์ ๋ณํํ์ฌ ์๋ก๋ํ๋ ์์์ ์งํ๋๋ ๊ฒ ๊ฐ์๊ณ  null์ธ ํ์ผ์ ๋ณํํ  ์ ์์ผ๋ ์ค๋ฅ๊ฐ ์๊ธด ๊ฒ ๊ฐ์๋ค.
		```java
		// 1. MultipartFile์ ์ ๋ฌ๋ฐ์ File๋ก ์ ํํ ํ์ S3์ ์๋ก๋  
		public String upload(MultipartFile multipartFile, String dirName) throws IOException {  
		    if(!multipartFile.isEmpty()) {  
		        isImage(multipartFile);  
		    } else return null;  
		  
		    File uploadFile = convert(multipartFile)  
		            .orElseThrow(() -> new IllegalArgumentException("ํ์ผ ๋ณํ์ ์คํจํ์์ต๋๋ค."));  
		  
		    return upload(uploadFile, dirName);  
		}
		```
		- multipartFile์ด ๋น์ด์์ผ๋ฉด null๊ฐ์ ๋ฐํํ๊ณ  ํ์ผ์ ๋ณํํ๋ ์์์ ๊ฑฐ์น์ง ์๋๋ก return ํ์๋ค.


2. ๊ฒ์๊ธ ์ญ์ ์ ์ด๋ฏธ์ง๋ S3์์ ์ญ์ ๋๊ฒ ํ๊ธฐ

	- ๋ฌธ์ ์  : ๊ฒ์๊ธ์ ์ญ์ ํด๋ S3 ์ ์ฅ์์๋ ์ฌ์ ํ ์ด๋ฏธ์ง ํ์ผ์ด ๋จ์์์ด์ URL๋ง ์๋ฉด ์ ๊ทผ์ด ๊ฐ๋ฅํ๊ณ , ์ญ์ ๋ ๊ฒ์๊ธ์ ์ด๋ฏธ์ง๋ ์ ์ฅ์์์ ์๋ฏธ์๋ ์ฉ๋์ ์ฐจ์งํ๊ณ  ์๊ธฐ์ ์ญ์ ๊ฐ ํ์ํ์๋ค.
	- S3 ์ ์ฅ์์ ํ์ผ์ ์ญ์ ํ  ๋ ํ์ํ ์์๋ ๊ฐ์ฒด์ Key๊ฐ์ด๋ฉฐ Key๊ฐ์ ๊ฐ์ฒด์ URL์์ ๋ฒํท์ฃผ์๋ฅผ ์ ์ธํ ๊ฐ์ด๋ค.(๋ญ๋๋ ๊ฑฐ์)
		- ๊ฐ์ฒด URL ์์
			- https://postblog-bucket.s3.ap-northeast-2.amazonaws.com/static/66baf610-cf7a-46fc-a54f-420fca739841notice.jpg
			- URL์ ์๋ก๋๋ฅผ ์งํํ๋ฉด์ ๋ค์๊ณผ ๊ฐ์ด ๋ฐ๋๋ค.
				- bucket์ฃผ์/ํด๋๊ฒฝ๋ก(dirName)/UUID๊ฐ+ํ์ผ์ด๋ฆ
				- static์ ํด๋๊ฒฝ๋ก์ด๊ณ  ๊ทธ ๋ท๋ถ๋ถ์ด UUID๊ฐ๊ณผ ํ์ผ์ด๋ฆ์ธ notice.jpg์ด๋ค.
		 - ๊ฐ์ฒด์ Key๊ฐ
			 - ์ฌ๊ธฐ์ ๊ฐ์ฒด์ Key๊ฐ์ bucket์ฃผ์๋ฅผ ์ ์ธํ ๋ถ๋ถ์ด๋ค.
			 - Key๊ฐ : static/66baf610-cf7a-46fc-a54f-420fca739841notice.jpg
	- ํ์ผ์ ์๋ก๋ํ๋ ๊ณผ์ ์์ string fileName์ด๋ผ๋ฉฐ Key๊ฐ์ด ๋ง๋ค์ด์ง๋๋ฐ ์ด ๊ฐ์ ์ด๋ป๊ฒ ๋ถ๋ฌ์์ผํ ์ง ๊ณ ๋ฏผ๋์๋ค.
	```java
	// 2. S3์ ํ์ผ ์๋ก๋ ํ๊ธฐ  
	//    fileName = S3์ ์ ์ฅ๋๋ ํ์ผ์ด๋ฆ(randomUUID๋ ํ์ผ์ด ๋ฎ์ด์์์ง์ง ์๊ธฐ ์ํจ)  
	//    1๋ฒ์ ์งํํ๋ฉด์ ๋ก์ปฌ์ ์์ฑ๋ ํ์ผ์ ์ญ์ ๊น์ง ํ๋ ํ๋ก์ธ์ค  
	private String upload(File uploadFile, String dirName) {  
	    String fileName = dirName + "/" + UUID.randomUUID() + uploadFile.getName();  
	    String uploadImageUrl = putS3(uploadFile, fileName);  
	  
	    removeNewFile(uploadFile);  
	  
	    return uploadImageUrl;  
	}
	```
	- PostRepository๋ฅผ ํ๋์ ๋ถ๋ฌ์จ ํ์ postRepostory์ fileName์ saveํ๋ ๋ฐฉ๋ฒ์ ํด๋ณด์์ง๋ง, ๊ทธ๋ฌ๋ฉด ์ ์ PostService์์ title๊ณผ imgUrl๊ฐ์ด ์ ์ฅ์ด ๋์ง ์์๋ค.

	- ๋ค์์ ๊ฒ์๊ธ ๋ฑ๋ก์ฒ๋ฆฌ ํ๋ ๊ณผ์ ์ด๋ค. ์ด ๋ถ๋ถ์์ postRepository์ title, imgUrl๊ณผ ํจ๊ป fileName(key๊ฐ)์ด ์ ์ฅ์ด ๋์ด์ผ ์ญ์ ๋ฅผ ํ  ๋ ํค ๊ฐ์ ๋ถ๋ฌ์ฌ ์ ์์ ๊ฒ ๊ฐ์๋ค.
	```java
	// ๊ฒ์๊ธ ๋ฑ๋ก ์ฒ๋ฆฌ  
	@Transactional  
	public PostResponseDto createPost(PostRequestDto postRequestDto, MultipartFile multipartFile) throws IOException {  
	  
	    String imgUrl = s3Uploader.upload(multipartFile, "soso");  
	    String fileName;  
	    if(imgUrl == null) {  
	        fileName = null;  
	    } else {  
	        fileName = imgUrl.substring(imgUrl.indexOf("soso"));  
	    }  
	    Post post = Post.builder()  
	            .title(postRequestDto.getTitle())  
	            .fileName(fileName)  
	            .imgUrl(imgUrl)  
	            .build();  
	    postRepository.save(post);  
	  
	    return PostResponseDto.builder()  
	            .id(post.getId())  
	            .title(post.getTitle())  
	            .imgUrl(post.getImgUrl())  
	            .createdAt(post.getCreatedAt())  
	            .modifiedAt(post.getModifiedAt())  
	            .build();  
	}
	```


	


	- ์์์๋ ์ค๋ชํ๋ฏ์ด ์ด๋ฏธ์งURL์ bucket์ฃผ์๋ฅผ ์ ์ธํด์ผ ํ๋ฏ๋ก, substring์ ์ด์ฉํ์ฌ ํด๋๊ฒฝ๋ก ์ ๊น์ง ์๋ฅด๊ณ  fileName์ด๋ผ๋ ๋ณ์์ ์ ์ฅํ์๋ค. ์ด ๋, Key๊ฐ๋๋ก ๊ฐ์ ์ ์ ์ฅ์ด ๋์์ผ๋ ์ด๋ฏธ์ง๋ฅผ ์๋ก๋ํ์ง ์์ ๊ฒฝ์ฐ imgURL์ด null์ธ๋ฐ null์ substringํ  ์๊ฐ ์์ผ๋ ์ค๋ฅ๊ฐ ์๊ฒผ๋ค.
	- ๊ทธ๋์ imgUrl์ด null๊ฐ์ด๋ฉด fileName๋ null์ ์ฃผ๊ณ , imgUrl์ด ์์ ๊ฒฝ์ฐ ๊ทธ url์ substringํด์ key๊ฐ์ ์ป์ ์ ์๋๋ก ํ์๋ค.

๊ธฐ์ ๋งค๋์ ๋์ด ์ฝ๋๋ฅผ ๋ณด์๊ณ ๋ ๋ค๋ฅธ ๋ฐฉ๋ฒ์ ๊ณ ๋ฏผํด๋ณด๋ผ๊ณ  ํ์๋ค. ๋์ญ์ ์ฝ๋๊ฐ ์ง์ ๋ถํ๊ณ  ๋ถ์ํ๋ ๋ถ๋ถ์ด๋ผ ์ข ๋ ๊ณต๋ถ๋ฅผ ํ ํ์ ์์ ์ ํด์ผํ  ๊ฒ ๊ฐ๋ค.


