# COMP4010/5120: Data Visualization - Spring 2025

# Instruction for Project 2

## 1. Project Details

The goal of this project is to apply what you have learnt throughout the semester to solve a very open-ended problem. Students will be assigned in teams, consisting of 3 members per team. In this project, your task is to create something related to data visualization. This is a vague prompt and you will find more info in the deliverables section of this document. The project will be completed over the second half of the semester and will account for 30% of your final score.

## 2. Project Timeline

- **Week 1 (17/04 - 27/04):** Meet your team, begin brainstorming ideas for your project; Submit your project proposal.
- **Week 2 (27/04 - 04/05):** Provide peer reviews to two other teams as issues on their GitHub repos. Address issues raised on your team’s project repo through explicit commits. Start working on coding, presentation, and report. (remember to take a break on 30/04 and 01/05 :D)
- **Week 3 (05/05 - 15/05):** Review feedback from the teaching team on your proposal and continue working on deliverables.
- **Week 4 (16/05 - 30/05):** Finalize your report and presentation, and clean up code files.

## 3. Deadlines

There are four important milestones for this project:

- **27/04:** Submit the first version of the project proposal.
- **04/05:** Complete peer reviews for two other teams.
- **15/05:** Resubmit the revised proposal based on peer reviews and resolve the issues raised.
- **30/05:** Submit the project package, including presentation slides, write-up, and code files.

## 4. Deliverables

### 4.1 Project Questions
One requirement is that your project should feature some element that you had to learn on your own. This could be a package you use that we didn’t teach in class (e.g., a package for building 3D visualizations) or a workflow (e.g., making a package) or anything else. Another requirement is that it cannot be an extension of you Data-Driven Story Project. So need to work on something completely different from that project and project 1. And the last requirement is that your project is built reproducibly in R. Your first task is to come up with a goal for your project. Here are a few ideas to help you get
started thinking:

- Build a Shiny app that that has an Instagram-like user interface for applying filters, except not filters but themes for ggplots.
- Create an R package that provides functionality for a set of ggplot2 themes and/or color palettes
- Build a generative art system.
- Do a deep dive into accessibility for data visualization and build a lesson plan for creating accessible visualizations with ggplot2, Quarto, and generally within the R ecosystem.
- Create an interactive and/or animated spatio-temporal visualization on a topic of interest to you, e.g., redistricting, COVID-19, voter suppression, etc.
- Recreate art pieces with ggplot2.
- Make a data visualization telling a story and convert it to an illustration, presenting both the computational and artistic piece side by side.
- Build a dashboard.
And, of course, your project can be about visualizing a dataset of interest to you (similar to your first project). The only rule about this dataset is that you need to be the one who create the dataset **(through crawling, for example)**. Furthermore, as we have already done this in project 1, if you choose this path and want to get decent score, you should attempt to visualize a very challenging dataset, such as creating visualization for 3+ dimensions, visualize social network, text, etc.. Plotting non-interactive charts and visualize a dataset with bar plot/ pie chart will not give you high score for project 2. 


### 4.2 Details on Deliverables

4.2 Details on deliverables
Proposal - Due 25th of April


Peer Review - Due 5th of May
Each team will review the proposals of two other teams. We will assign which teams that you
have to write the reviews for (check section 6.3 of this document)
Teams will develop the review together, with discussion among all team members, but only
one team member will submit it as an issue on the project repo. To do so, go to the Issues
tab, click on the green New issue button on the top right.
The title of the issue should be “Peer review for proposal - [Your group name]”, and you
should point out 2-3 problems or suggestions for your friends to improve their work.
Remember, your goal is to help the team whose project proposal you’re reviewing. The team
will not lose points because of issues you point out, as long as they address them before I
review their proposals. You should be critical, but respectful in your review. Also remember
that you will be evaluated on the quality of your review. So that’s an additional incentive to do
a good job.
The expected output of this phases include:
- Create 2 issues on the repositories of each of the 2 teams you are assigned to
review
- Submit links to the issues you have created on your classmates’ repos
Replies to your feedback - Due 12th of May
Once you receive feedback from your peers, you should address them. You should do this
by directly updating your proposal or making any other updates to your repo as needed.
After addressing the feedback, you should also wrap up your updates with a comment,
detailing on how you are going to fix the problems/suggestions made by your friends.
The expected output of this phases include:
- Commits and comments on the repositories to address the issues your peers point
out
- (Optional) Revise your proposal and TAs will give you feedback on the new version,
but this task is not graded
Write-up - Due 2nd of June
Your have a lot more freedom in how you structure your write-up for this project compared to
Project 1. This also comes with responsibility. You should make sure you have a clear
introduction and a clear conclusion. You should also have other interim section headings that
help the reader. Your write-up should be somewhere between 1000 and 2000 words. There
is no expectation that you get close to the upper limit, anywhere in that range is fine as long
as you have clearly explained yourself. The limits are provided to help you, not to set
stressful expectations.
The expected output of this phases include:
- Submit your report on canvas in RmD/ Pdf format
- Your code for the project should be well documented and reproducible, i.e. we can
retrieve the same output which you present through running your code
Presentation - Slides due 2nd of June, Oral Presentation due the following week
Each team will give a 12-minute presentation, followed by Q&A. We expect each
presentation + Q&A will last within 20 minutes.
And of course, this presentation should include a demo of your product if you are building
dashboard, package, etc.
The expected output of this phases include:
- Submit your slides on canvas (pdf or ppt)
- In-class presentation followed by Q&As
Group contribution form - Due 2nd of June
Follow this template, submit a copy of your team contribution on Canvas. Your individual
score will be weighted based on this document.
The expected output of this task include:
- A document detailing your team contribution

#### **📌Proposal - Due 27th of April**

Your proposal should include:

1. A one sentence description of your high-level goal (such as the ones listed above).
2. A one to two paragraph description of your goals, including your motivation. Please explain why this project is interesting, what problems can it solve? 

   Depending on the focus of your project, the following might go in here:
      - If answering a particular research question, the question itself and the reason why you chose this question.
      - If you crawl a new dataset and plan to visualize it, explain how you collect the data, why you choose to tackle this problem and any other relevant metadata. 

3. A weekly plan outlining your steps to complete your project and including the team member(s) assigned to that task.
4. A github repo, with all the relevant info about your project

The expected output of this phases include:
- Create a public repository on Github
- Upload your proposal and data to that repository. Proposal can be a .md file
- Submit the link to your repository on Canvas by the deadline

👉*Expected output:*

- Create a public repository on GitHub.
- Upload your proposal and data to the repository (proposal can be a .md file).
- Submit the repository link on Canvas.

#### **📌Peer Review - Due 25th of March**

Each team will review the proposals of two other teams. We will assign review pairs (see Section 6.3 of this document).

**Review Process:**

- Develop the review as a team.
- One member will submit it as an issue on the reviewed team’s project repo.
- Title the issue: `Peer review for proposal - [Your group name]`.
- Provide 2-3 constructive suggestions.

👉*Expected output:*

- Create two issues on the repositories of the teams assigned to you.
- Submit links to the issues on Canvas.

#### **📌Revised Proposal - Due 31st of March**

After receiving feedback, update your proposal and make necessary revisions.

👉*Expected output:*

- Commits and comments addressing the issues raised.
- Submit the final version of the proposal on Canvas (PDF format).
- Submit links to addressed issues on your repository.

#### **📌Write-up - Due 10th of April**

The write-up consists of three parts:

1. **Introduction:** Briefly introduce the dataset and its importance.
2. **Question 1 Analysis:**
   - Introduction to the question and relevant dataset components.
   - Approach: Describe types of plots (boxplot, barplot, etc.) and their relevance.
   - Analysis: Code snippets and visualizations.
   - Discussion: Interpretation of results.
3. **Question 2 Analysis:** Same structure as Question 1.
4. **Conclusion:** Summary of findings and next steps.

👉*Expected output:*

- Submit the report on Canvas in Jupyter Notebook and PDF format.
- Ensure the report is well-documented and reproducible.

#### **📌Presentation - Slides Due 10th of April, Oral Presentation in the Following Week**

Each team will give an **8-minute presentation**, followed by **Q&A**. The session will last **15 minutes** in total.

👉*Expected output:*

- Submit slides on Canvas (PDF or PPT format).
- Deliver an in-class presentation with a Q&A session.

## 5. Grading

| Category              | Points  | Percentage |
|----------------------|---------|------------|
| Proposal            | 10 pts  | 10%        |
| Revised Proposal    | 10 pts  | 10%        |
| Peer-review Quality | 10 pts  | 10%        |
| Write-up           | 35 pts  | 35%        |
| Presentation       | 35 pts  | 35%        |
| **Total**          | **100 pts** | **100%** |

The marking scheme will be provided on the Canvas assignment page of each assessment.
## 6. Group
### PROJECT01-1 
- Pham Quoc Cuong
- Phan Minh Tri

### PROJECT01-2 
- Le Minh Huyen
- Vu Tuyet Vy

### PROJECT01-3 
- Ta Quang Hieu
- Nguyen Tien Dong

### PROJECT01-4 
- Doan Quang Hung
- Ngo Sy Trung

### PROJECT01-5 
- Mai Tuan Minh
- Tran Trung Duc

### PROJECT01-6
- Le Gia Duc
- Samantha Emma Morris
- Vo Khoi Thanh Lam

### PROJECT01-7
- Cao Lam Huy
- 
- Nguyen Canh Huy

### PROJECT01-8
- Thai Minh Dung
- Tran Khanh Bang
- Truong Dang Gia Huy

### PROJECT01-9
- Nguyen Hoang Long
- Nguyen Tuan Hiep
- Vu Ai Thanh

### PROJECT01-10
- Nguyen Nhat Minh
- Nguyen Truong Tung
- Nguyen Tung Lam

### PROJECT01-11
- Can Ha An
- Dao Chi Tuong
- Luu Nguyen Chi Duc

### PROJECT01-12
- Bui Huy Linh Phuc
- Dang Dinh Dang Khoa
- Ha Minh Dung

### PROJECT01-13
- Thai Ba Hung
- Tran Le Hai
- Dang Duc Dat

### PROJECT01-14
- Ekaterina Balashova
- Le Nguyen Gia Binh
- Vuong Chi Hao

### PROJECT01-15
- Nguyen Hoang Son
- Tran Hung Dat
- Tran Tat Hung

### PROJECT01-16
- Chau Minh Khai
- Nguyen Tuan Anh
- Ta Viet Thang

### PROJECT01-17
- Nguyen Mau Hoang Hiep
- Pham Minh Hieu
- Phan Thi Hien Chi



4. Deliverables

5. Grading