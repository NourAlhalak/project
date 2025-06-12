#project

import React, { useState } from 'react';
import './App.css';

const students = [
  { name: "Aiden Carter", level: 1, averageScore: 88 },
  { name: "Bella Thompson", level: 2, averageScore: 91 },
  { name: "Caleb Johnson", level: 3, averageScore: 84 },
  { name: "Daisy Nguyen", level: 3, averageScore: 93 },
  { name: "Ethan Wright", level: 1, averageScore: 76 },
  { name: "Fiona Lopez", level: 3, averageScore: 89 },
  { name: "Gavin Smith", level: 2, averageScore: 82 },
  { name: "Hannah Patel", level: 3, averageScore: 95 },
  { name: "Isaac Chen", level: 1, averageScore: 79 },
  { name: "Jasmine Rivera", level: 2, averageScore: 87 }
];

const App = () => {
  const [selectedLevel, setSelectedLevel] = useState("all");

  const handleLevelChange = (e) => setSelectedLevel(e.target.value);

  const filteredStudents = selectedLevel === "all"
    ? students
    : students.filter(student => student.level === parseInt(selectedLevel));

  return (
    <div style={styles.container}>
      <h2 style={styles.heading}>Students Table</h2>
      <label style={styles.filterLabel}>
        Filter by level:
        <select 
          value={selectedLevel} 
          onChange={handleLevelChange} 
          style={styles.select}
        >
          <option value="all">All</option>
          <option value="1">Level 1</option>
          <option value="2">Level 2</option>
          <option value="3">Level 3</option>
        </select>
      </label>
      <table style={styles.table}>
        <thead>
          <tr style={styles.tableHeader}>
            <th style={styles.tableCell}>Name</th>
            <th style={styles.tableCell}>Level</th>
            <th style={styles.tableCell}>Average Score</th>
          </tr>
        </thead>
        <tbody>
          {filteredStudents.map((student, index) => (
            <tr 
              key={index} 
              style={{
                ...styles.tableRow,
                backgroundColor: index % 2 === 0 ? '#f4f4f4' : '#fff'
              }}
            >
              <td style={styles.tableCell}>{student.name}</td>
              <td style={styles.tableCell}>{student.level}</td>
              <td style={styles.tableCell}>{student.averageScore}</td>
            </tr>
          ))}
        </tbody>
      </table>
    </div>
  );
};

const styles = {
  container: {
    maxWidth: '900px',
    margin: '50px auto',
    padding: '20px',
    backgroundColor: '#f9f9f9',
    borderRadius: '8px',
    boxShadow: '0 4px 10px rgba(0, 0, 0, 0.1)',
  },
  heading: {
    fontSize: '24px',
    color: '#333',
    marginBottom: '20px',
    textAlign: 'center',
  },
  filterLabel: {
    fontSize: '16px',
    color: '#555',
    display: 'block',
    marginBottom: '15px',
  },
  select: {
    padding: '10px',
    fontSize: '16px',
    marginLeft: '10px',
    borderRadius: '5px',
    border: '1px solid #ccc',
  },
  table: {
    width: '100%',
    borderCollapse: 'collapse',
    marginTop: '20px',
  },
  tableHeader: {
    backgroundColor: '#007bff',
    color: '#fff',
    fontWeight: 'bold',
  },
  tableCell: {
    border: '1px solid #ddd',
    padding: '12px 15px',
    textAlign: 'left',
  },
  tableRow: {
    transition: 'background-color 0.3s ease-in-out',
  },
};

export default App;
