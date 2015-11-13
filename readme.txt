. I have created a new repository PRODSUP-002 and I imported tgere Case2  https://github.com/nym2015/commons-csv  my public GitHub path is : https://github.com/viliescu/PRODSUP-002.git
In entered in CircleCI and access my account and set Build Project for PRODSUP-002. After generating the public key I saw that the new Project appears in Circleci but the build is not done.
2. The problem is caused by missing the master default branch. So I created a master branch identically like trunk and set this master branch as default.
3. In Cirleci build was started revision 7005c27 - most time consuming phase is $ mvn integration-test - on Running org.apache.commons.csv.LexerTest timed out after 2 hours - I investigated and found out that folder payth was missing so I added in circle.yml  :
general:
  build_dir: src
After rebuilding - tests were fine in Circleci for both branches : trunk and master; I have also cancel old wrong configured tests. I received on email that the problem was fixed :)

Mail received :

Fixed! Fixed	
build report	viliescu/PRODSUP-002 #11
branch	master
commits	Update circle.yml 9f70f95 
author	viliescu
Yay, all your tests have passed!
Your commands (they all ran successfully):
Starting the build
Start container
Enable SSH
Restore source cache
Checkout using deploy key: a9:66:4d:e3:5f:bb:42:8d:56:a8:70:fc:be:a0:13:06
Configure the build
Restore cache
Save cache
mkdir -p $CIRCLE_TEST_REPORTS/junit/
find . -type f -regex ".*/target/surefire-reports/.*xml" -exec cp {} $CIRCLE_TEST_REPORTS/junit/ \;
Collect test metadata
Collect artifacts
Disable SSH
