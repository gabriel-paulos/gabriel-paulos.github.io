# My personal web-page

This is a static [HUGO](https://gohugo.io) web-page hosted using AWS S3, and
deployed using [Terraform](https://www.terraform.io) to create a reproducible
pipeline. In short, I used AWS CodePipeline and CodeBuild to automatically
update the web-page contents each time I pushed to the `master` branch. Sounds
nice, right? 

### Automated infraestructure

Terraform file (`.ws-cicd-with-github-test.tf`) creates the needed AWS pieces to
make this happen. First, AWS will create a temporary S3 bucket to contain the
source code, and to fetch the data to CodeBuild. CodeBuild will create
a temporary AMI, configured using the `buildspec.yml` file, and output the
contents to a web-hosting S3 bucket. 

### More magic behind

AWS has amazing features! Using Route53, is really easy to have an SSL
certificate, and configure Cloudfront to distribute traffic and use `https` (you
have to be careful out there :wink:).

### To-Do
 - A more detailed documentation
 - Automate HUGO theme cloning (I made a hack, CodeBuild do not `git clone` the
   repo, but `.zip` its contents and remove the `.git` [weird behavior])

