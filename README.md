# DA-Task4

dataset:

![image](https://github.com/user-attachments/assets/4fe5ea6a-0dcd-40a9-a869-97bbe345d444)

(a) Basic SQL Queries: SELECT, WHERE, ORDER BY, GROUP BY

1. select * from athlete_events limit 15;
   
Explanation: Fetches the first 10 rows from the table to give you a quick look at the data.

![Screenshot (547)](https://github.com/user-attachments/assets/9502ca56-4c56-4e55-a26e-dac3d48689a1)

2. select Name, Sport, Medal, Season
   
from athlete_events

where year = 2012;

Explanation: Lists names, sports, and teams of all athletes who took part in the 2012 Olympics.

![Screenshot (548)](https://github.com/user-attachments/assets/05b1ff8c-a5a1-4251-9e21-07bfd2a4cc0a)


3. select Name, Sport, Medal, Team
   
from athlete_events

order by Age

limit 15;

Explanation: Shows the oldest 10 athletes, with their names, ages, and teams.

![Screenshot (549)](https://github.com/user-attachments/assets/e9ba6e87-12e9-4dba-b266-ac11389714d1)


6. select Sport, count(*) as athlete_count
   
from athlete_events

group by Sport

order by athlete_count desc;

Explanation: Counts how many athletes participated in each sport and sorts them by most popular sport first.

![Screenshot (550)](https://github.com/user-attachments/assets/2fb3ece7-a3e5-4d42-9f13-1a166c996923)


7. SELECT a1.Name, a1.Sport, a2.Year
   
FROM athlete_events a1

INNER JOIN athlete_events a2

ON a1.ID = a2.ID

WHERE a1.Medal = 'Gold' AND a2.Year = 2016

LIMIT 10;

Explanation:

    Joins the table with itself (a1, a2) using the athlete ID

    Filters athletes who won Gold and also appeared in 2016

    Shows name, sport, and year

![Screenshot (551)](https://github.com/user-attachments/assets/28687d79-d47d-4993-9129-047323cc1886)


8. SELECT Name, Age
   
FROM athlete_events

WHERE Age > (SELECT AVG(Age) FROM athlete_events);

Explanation: Finds all athletes whose age is greater than the average age of all athletes.

![Screenshot (552)](https://github.com/user-attachments/assets/5f8adacf-9cc6-422c-8809-2cca9749e477)


9. SELECT Sport, COUNT(*) AS gold_medals
    
FROM athlete_events

WHERE Medal = 'Gold'

GROUP BY Sport

ORDER BY gold_medals DESC

LIMIT 1;

Explanation: Groups by sport, counts how many gold medals each sport got, and shows the top sport with most golds.

![Screenshot (553)](https://github.com/user-attachments/assets/64abf106-318d-47bb-a083-0cbf3f6e8063)


10. SELECT Sport, AVG(Height) AS avg_height
    
FROM athlete_events

GROUP BY Sport;

Explanation: Calculates the average height of athletes in each sport.

![Screenshot (554)](https://github.com/user-attachments/assets/eba1be45-ba17-4733-8c8e-4c3fae967f28)


11. SELECT Team, COUNT(*) AS total_medals
    
FROM athlete_events

WHERE Medal != 'N/A'

GROUP BY Team

ORDER BY total_medals DESC

LIMIT 10;

Explanation: Counts how many medals each team won (excluding N/A) and lists the top 10 teams.

![Screenshot (555)](https://github.com/user-attachments/assets/743dfbae-488e-40df-99d2-387730788c27)


12. CREATE VIEW MedalWinners AS
    
SELECT Name, Sport, Team, Medal, Year

FROM athlete_events

WHERE Medal IS NOT NULL AND Medal != 'N/A';

Explanation:

    Creates a virtual table called MedalWinners

    It stores a filtered view of athletes who actually won medals

    You can query it like a regular table:

SELECT * FROM MedalWinners LIMIT 10;

![Screenshot (556)](https://github.com/user-attachments/assets/ffb1745e-76b9-428c-a32c-f240ffa25332)


13. CREATE INDEX idx_team_year ON athlete_events(Team, Year);

Explanation: Adds an index on the Medal column so that queries filtering by medal (e.g., WHERE Medal = 'Gold') run faster.

![Screenshot (557)](https://github.com/user-attachments/assets/753a699d-1912-4944-ba10-b36d68d8ebc5)


14. CREATE INDEX idx_medal ON athlete_events(Medal);

Explanation: Creates a multi-column index on Team and Year to speed up queries involving both.

![Screenshot (558)](https://github.com/user-attachments/assets/7480ac88-13df-46ac-ab90-987d5fab7a8c)

To check which indexes exist:
PRAGMA index_list('athlete_events');

![Screenshot (559)](https://github.com/user-attachments/assets/bb95b1a5-369d-40a2-9406-db1510be24ec)







