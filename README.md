# translator-react
How we can implement multi language supportive in React js

**1. install below packages**

"i18next": "^15.0.9",

"i18next-browser-languagedetector": "^3.0.1",

"i18next-xhr-backend": "^3.0.1",

"react-i18next": "^11.7.4",


**2. Create tranlastion object in below location**
     ===public\assets\i18n\translations\en.json====
      ===public\assets\i18n\translations\th.json==== 
          {
           "phoneno.label": "Phone number",
          }
**3. create same file as i18.js which is available in this project**

**4. How to create a connection between React component and i18n translatior**
    import { useTranslation } from "react-i18next";
    
    ===inside component function=== Header
const { i18n } = useTranslation();
const { t } = useTranslation();
  React.useEffect(() => {
      setTimeout(() => {
      if (
        localStorage.getItem("lancode") &&
        localStorage.getItem("lancode") !== ""
      ) {
      } else {
        localStorage.setItem("lancode", "th");
        i18n.changeLanguage("th");
      }
    }, 2000);
   
  }, []);
  
  =======click event when langauge will be changed========
          const changeLanguage = (e, value) => {
          localStorage.setItem("lancode", value);
          i18n.changeLanguage(value);
        };
        
 ========= map all component with i18==========
 import { useTranslation, withTranslation } from "react-i18next";
 
  ===inside component function===
 const { t } = useTranslation();
 
 ====== inside render funciton function ==========
 <h2>{t("firstTimeLogin.label")}</h2>
 
 ====    export any react component with i18n ====
 export default withTranslation()(AddUserSelection);
 
** 5. dynamic language change with api response data...**

{lancode === "th" && (
<>{items.myNameTH}</>
)}
{lancode === "en" && (
<>{items.myNameEN}</>    
)}
<!-- myNameEN, myNameTH is a api response onject name -->
 

