# DogDayCare

/////////////////////////////////////////////////////////////
//      A Console Application that runs queries for        //
//      Dog day cares.                                     //
//                                                         //
/////////////////////////////////////////////////////////////


## The Queries we chose:

1. Return all daycares along with their city and state

Select dc.DaycareName, c.CityName, s.StateAbbr
FROM OakesDB.Daycare dc INNER JOIN OakesDB.City c ON dc.LocationID INNER JOIN OakesDB.State s on dc.StateID = s.idState;
# DaycareName, CityName, StateAbbr
'Dog City West', 'Battleground', 'WA'
'Good Doggy Day Care', 'Battleground', 'WA'
'Tails of the City', 'Battleground', 'WA'

2. Return types of grooming offered by all daycares in Seattle

SELECT DC.DaycareName, SS.SubServiceName
FROM OakesDB.Daycare DC INNER JOIN OakesDB.DaycaretoService DS ON DC.DaycareID = DS.DaycareID INNER JOIN
OakesDB.ServiceCategory SC ON DS.ServiceID = SC.ServiceCatID INNER JOIN
OakesDB.City C ON C.LocationID = DC.LocationID INNER JOIN
OakesDB.SubService SS ON SS.ServiceID = DS.ServiceID AND DS.SubServiceID = SS.ServiceSubCatID
WHERE SC.CategoryName = "Grooming"
AND C.CityName = "Bellevue";
# DaycareName, SubServiceName
'Dog City West', 'Bath and Brush'

3. Return all daycares which offer boarding and have webcams

SELECT DC.DaycareName, C.CityName
FROM OakesDB.Daycare DC INNER JOIN OakesDB.City C ON DC.LocationID = C.LocationID INNER JOIN
OakesDB.DaycareToAmmenity DA ON DC.DaycareID = DA.DaycareID INNER JOIN
OakesDB.AmmenitiesProvided AP ON DA.AmmenityID = AP.idAmmenityID
WHERE AP.AmmenityDesc = "Webcam";
# DaycareName, CityName
'Dog City West', 'Bellevue'
'DogTopia', 'San Francisco'
'Rain City Day Care', 'Seattle'
'Tails of the City', 'Seattle'
'WoofPlayAndStay', 'Olympia'

