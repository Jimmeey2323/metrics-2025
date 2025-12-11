# ZIP File Format Support

The Physique 57 Analytics Dashboard now supports multiple ZIP file formats for CSV data processing.

## Supported Formats

### Format 1: Original Format
- Files ending with `aggregate.csv`
- Columns: `'Teacher First Name'`, `'Teacher Last Name'`, `'Class name'`, `'Class date'`, `'Checked in'`
- Multiple individual aggregate files per teacher

### Format 2: New Momence Format
- Combined aggregate file: `momence-teachers-payroll-report-aggregate-combined.csv`
- Individual aggregate files: `*-aggregate.csv`
- Columns: `'Instructor First Name'`, `'Instructor Last Name'`, `'Class Name'`, `'Class Date'`, `'Checked in'`
- Additional columns: `'Participants'`, `'Total Revenue'`, etc.

## Processing Logic

The script automatically detects the format and processes accordingly:

1. **Primary**: Looks for combined aggregate file (`*aggregate-combined.csv`)
2. **Secondary**: Looks for individual aggregate files (`*aggregate.csv`)
3. **Fallback**: Processes any available CSV files

## Column Mapping

| Original Format | New Format | Purpose |
|----------------|------------|---------|
| `Teacher First Name` | `Instructor First Name` | Teacher's first name |
| `Teacher Last Name` | `Instructor Last Name` | Teacher's last name |
| `Class name` | `Class Name` | Session/class name |
| `Class date` | `Class Date` | Date of the class |
| `Checked in` | `Checked in` | Number of attendees |

## Automatic Detection

The script automatically:
- Detects column name variations
- Handles different file naming patterns
- Falls back to alternative columns if primary ones are missing
- Provides detailed processing feedback via notifications

## Error Handling

- Shows specific error messages for different failure scenarios
- Provides progress feedback during processing
- Validates data integrity before displaying results
- Gracefully handles corrupted or invalid files