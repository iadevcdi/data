# Specifications 
- Including fall detection, the **Posture** column should indicate not only standard postures (such as standing, sitting, lying down) but also specify if a fall has been detected. 
- Here are the modifications to reflect this update:

---

### **3. Data Structure - Posture Column Update**

2. **Columns and Data Types** (updated):

   | **Column Name**         | **Description**                                                                | **Expected Format**     | **Example**              |
   |--------------------------|--------------------------------------------------------------------------------|-------------------------|--------------------------|
   | **Timestamp**            | Precise time of each image in the sequence                                     | `hh:mm:ss` or `ms` from start | `02:05:12`             |
   | **Date**                 | Date of movement capture                                                      | `YYYY-MM-DD`           | `2024-10-15`             |
   | **Coordinates_x1**       | X coordinate of key point 1 (e.g., hip)                                       | `Float`                | `100.5`                  |
   | **Coordinates_y1**       | Y coordinate of key point 1                                                   | `Float`                | `150.2`                  |
   | **Coordinates_z1**       | Z coordinate of key point 1                                                   | `Float`                | `0.5`                    |
   | **Coordinates_xN**       | X coordinate of the last key point (e.g., ankle)                              | `Float`                | `98.7`                   |
   | **Posture**              | Current posture of the person (`standing`, `sitting`, `lying`, `fall`)        | `String`               | `fall`                   |
   | **Blanket Status**       | Status of the blanket (`Blanket On` or `Blanket Off`)                         | `String`               | `Blanket Off`            |
   | **Action Status**        | Ongoing action (`getting up`, `walking`, `fall`)                              | `String`               | `Wokeup`                 |

3. **Example CSV Line**:

   ```
   Timestamp,Date,Coordinates_x1,Coordinates_y1,Coordinates_z1,...,Posture,Blanket_Status,Action_Status
   12,2024-10-15,100.5,150.2,0.5,...,fall,BlanketOff,Fell
   ```

---

By incorporating "fall" into the **Posture** column in the CSV file, the LSTM model will be better equipped to differentiate between normal movements and anomalies, such as falls, and more effectively classify these events within the temporal flow of sequences.
