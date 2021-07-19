# Translate
public class LangTranslation { 

  

    public static Map<String, String> setMapData() throws IOException { 

  

          String path = "data/TestDataSheet.xlsx"; 
           
          FileInputStream fis = new FileInputStream(path); 
     
          Workbook workbook = new XSSFWorkbook(fis); 
         
          Sheet sheet = workbook.getSheetAt(0); 
           
          int lastRow = sheet.getLastRowNum(); 
           
           
          Map<String, String> dataMap = new HashMap<String, String>(); 
           
          //Looping over entire row 
          for(int i=0; i<=lastRow; i++){ 
               
              Row row = sheet.getRow(i); 
               
              //1st Cell as Value 
              Cell valueCell = row.getCell(1); 
                   
              //0th Cell as Key 
              Cell keyCell = row.getCell(0); 
                   
              String value = valueCell.getStringCellValue().trim(); 
              String key = keyCell.getStringCellValue().trim(); 
                   
              //Putting key & value in dataMap 
              dataMap.put(key, value); 
                   
     
          } 
          
        return dataMap; 
    } 

  

  

    public static void main(String[] args) throws IOException { 
        LangTranslation r = new LangTranslation(); 
        Map<String, String> transWordMap = r.setMapData(); 
         
Scanner s = new Scanner(new File("filepath")); 
ArrayList<String> englishList = new ArrayList<String>(); 
while (s.hasNext()){ 
    englishList.add(s.next()); 
} 
s.close(); 

  

ArrayList<String>  translatedList = new ArrayList<String>(); 

  

if (!englishList.isEmpty()) 
{ 

  

for (String key :englishList)  
{ 
     String value=transWordMap.get(key)!=null ? transWordMap.get(key).toString():key; 
     translatedList.add(value);      
} 
} 
FileWriter writer = new FileWriter("output.txt");  
for(String str: translatedList) { 
  writer.write(str + System.lineSeparator()); 
} 
writer.close(); 

  

  


    } 

  

} 

