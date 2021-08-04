# Øvelsesvejledning til øvelse 2 - navigation

#### Slut resultat
HER SKAL DER INDSÆTTES EN gif

## Del 1 - Tab Navigator

1. Start med at oprette et nyt projekt.
    - `expo init <--angiv navnet på øvelsen-->`
2. Installér følgende dependencies;
<ul>
    <li>@react-navigation/bottom-tabs</li>
    <li>@react-navigation/native</li>
    <li>@react-navigation/stack</li>
    <li>react-native-gesture-handler</li>
    <li>react-native-safe-area-context</li>
    <li>react-native-screens</li>
    <li>react-native-vector-icons</li>
            <ul><li>Et skærmklip af package.json filen fra den endelige løsning er vedlagt i bilag A.
                Din package.json bør være ens med denne efter installeringen. </li>
            <li>KOPIER linjen herunder til installering;</li>
                </ul>
    </ul>

    
             npm install --save @react-navigation/bottom-tabs @react-navigation/bottom-tabs @react-navigation/native @react-navigation/stack react-native-gesture-handler react-native-safe-area-context react-native-screens react-native-vector-icons



3. Opret en mappe og døb denne 'components'
4. I mappen oprettes tre js-filer(komponenter), der kaldes;<br/>  `HomeScreen`, `SettingsScreen` & `DetailsScreen`
    - Opret i hver af de tre komponenter en tekstkomponent, `<Text><--indhold--></Text>`, med et vilkårligt indhold 
5. Gå nu ind i app.json filen og importer de nyopretterede filer. 
6. Inden vi opretter en tabnavigator skal vi omskrive App.js fra at være en klassekomponent til at være en funktionel komponent.  
7. Når dette er sket, er du klar til at konstruere en bottomTabnavigator. 
   - Opret først en `const Tab` og lad denne være en instans af `createBottomTabNavigator()`
        - HUSK: `createBottomTabNavigator()` bør automatisk blive importeret. Er dette ikke tilfældet skal metoden importeres fra `@react-navigation/bottom-tab`
    - I `App` komponenten oprettes der i `return()`en `<NavigationContainer/>`, hvori en `<Tab.Navigator/>`oprettes. 
        - Sidder du fast er strukturen vedlagt i bilag B.
        - Derudover er der god hjælp i Expo's dokumentation, der kan findes på følgende link:
          https://reactnavigation.org/docs/tab-based-navigation/
    - Endeligt færdiggøres Tabnavigatoren ved at oprette tre `<Tab.Screen/>` komponenter i den oprettede `<Tab.Navigator/>`. 
        - Hver enkelt `<Tab.Screen/>` komponent har to properties; `name` & `component`. 
            - `name`: angiver et referencenavn(det er  et vilkårligt rutenavn, f.eks. "home" ) til den komponent, som kobles på den enkelte screen. 
            - `component`: Heri placeres den komponent, som man ønsker skal fremvises for den pågældende Tab
                - HINT: Igen, hvis du går i stå, så ta' et kig på dokumentationen, der kan findes på det førnævnte link.
8. Start din app og brug de tre oprettede tabs til at navigere mellem de forskellige Screens . 

## Del 2 - Stack Navigator
1.  Opret i `components` en ny fil, der kaldes `StackNavigator`. Derudover skal der i `components` mappen oprettes en ny mappe, der kaldes `StackComponents`. I denne mappe, skal der oprettes to nye js-filer med vilkårlige navne.<br/>HINT: Se struktur i bilag C
2. Gå nu ind i StackNavigator filen og omskriv klassekomponenten til en funktionel komponent, som gjort tidligere. 
3. Opret en `const Stack`. Denne skal være en instans af `createStackNavigator()`, der bør blive importeret automatisk.<br/>HINT: Dette er samme fremgangsmåde, som den der blev gennemført i punkt 7 i del 1.
4. I `return()` skal der oprettes en komponent, `<Stack.Navigator></Stack.Navigator>`
5. Opret nu tre `<Stack.Screen/>` komponenter i `Stack.Navigatoren`. Hver af de tre screen Komponenter indeholder igen properties i form af `name` og `component`, der har               samme betydning, som tidligere beskrevet.
6. Referér til `DetailsScreen` og komponenterne fra `stackcomponents`mappen        
7. StackNavigatoren er hermed lavet, hvorfor du nu skal vende tibage til App.js
8. Heri importereres `Stacknavigator`. Gå derefter ned ned til den `<Tab.Screen/>` som refererer til `DetailsScreen`. Erstat nu referencen til `DetailsScreen` med den      importerede `<StackNavigator/>.`<br>HUSK at opdatere `name` med en sigende reference betegnelse for StackNavigatoren<br/>
        HINT: Sidder du fast eller har udfordringer, så ta' et kig på dokumentationen: https://reactnavigation.org/docs/stack-navigator/
           
 9.  Gå nu ind i `DetailsScreen` og sørg for at denne modtager `navigation` som argument
 10. Dernæst skal metoden, `const navController = (navigation, route) => {}`, oprettes. Denne skal styre navigationen i Stacknavigatoren.
     - Logikken i metoden skal kalde den prædefinerede metode `navigate` på `navigation` og tage `route` med som argument til metoden<br/>HINT: Brug dokumentationen, hvis du         sidder fast:  https://reactnavigation.org/docs/navigating/<br/>Psst Psst.. Du kan også kigge i punkt 16. 
     
 11. Opet nu to `<Button/>` komponenter, som i onPress aktiverer `navController`. <br/>
        HUSK at rutenavnet, der tilføjes til metoden, skal passe med de rutenavne der blev angivet i `<Stack.Screen/>` komponenterne.<br/>HUSK derudover at sende `navigation`           med som argument.
     
 12. Endeligt skal navigationen i de to komponenter, der er placeret i `stackComponents` laves.
       - Naviger derfor til denne fil.
 13. Komponenten skal tage 'navigation' med som argument, som vist tidligere i `DetailsScreen`.
 14. I `return()` oprettes to `<Button/>` - ligesom i  `DetailsScreen`.
 15. Den ene `<Button/>` skal i onPress aktivere `navigation.goBack` - Dette er en tilbage-knap
 16. Den anden `<Button/>`  skal kalde `navigation.navigate(<--Rutenavnet på den anden screen i stackComponents-->)`
 17. Nu er øvelse færdig og du er klar til at prøve appen. Start din app op og forsøg at trykke på Details, som refererer til den nyoprettede `Stacknavigator`. I denne screen kan du se to knapper, der giver dig mulighed for at navigere ind til de to screens i stackComponents-mappen.     
 
## Videre arbejde - Inspiration
 - Placer ikoner på alle tabs
      - PLUS: Lav den valgte tab, så den har en anden farve, end resterende.<br/>HINT: Der er RIGTIG GOD hjælp at hente i dokumentationen nævnt i punkt 7 under konstruktionen af Tabnavigatoren
- Lav to tekststrenge til HomeScreen & DetailsScreen, som overføres til komponenternes Tekstkomponenter og fremvises.<br/>
     HINT: Rigtig god at hjælpe i følgende link: https://stackoverflow.com/questions/60439210/how-to-pass-props-to-screen-component-with-a-tab-navigator
- Bestem placering af Headerteksten vist i Stacknavigatoren, 'center', 'left' & 'right'.<br/>HINT: God hjælp at hente i dokumentationen, der er nævnt i punkt 4 under konstruktionen af StackNavigatoren(kig efter options).

## Bilag


### Bilag A - Package.json - Fra Endelig Løsning 

![img](https://user-images.githubusercontent.com/55731954/128073224-323544b0-0579-4e71-a6a9-c7ac6367a592.png)

### Bilag B - Bottom Tab struktur 

![img_1](https://user-images.githubusercontent.com/55731954/128073347-2d5699e3-c082-4d43-b96a-26503a07376d.png)

### Bilag C - Mappestruktur med stackcomponents
<img width="421" alt="asasdUdklip" src="https://user-images.githubusercontent.com/55731954/128073571-187b08bf-883a-4ffa-ac94-bcd2f6234f9b.PNG">
![5ihkps](https://user-images.githubusercontent.com/55731954/128075112-08c88318-188d-485d-898f-bf5cca6c9ebd.gif)





