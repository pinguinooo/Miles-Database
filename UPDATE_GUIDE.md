# How to Update the Car Database

## Quick Update Steps

1. **Add/Update the `version` field** at the top of your JSON file:
   ```json
   {
     "version": 2,
     "years": [...],
     "makes": [...]
   }
   ```

2. **Increment the version number** each time you make changes:
   - First version: `"version": 1`
   - After adding cars: `"version": 2`
   - After fixing data: `"version": 3`
   - etc.

3. **Commit and push** to GitHub:
   ```bash
   git add car-database.json
   git commit -m "Update database to version 2"
   git push
   ```

4. **Users will be prompted** to update when they launch the app!

## What You Can Update

### Add New Makes
Add a new make object to the `makes` array:
```json
{
  "name": "NewBrand",
  "models": [...]
}
```

### Add New Models
Add a new model to a make's `models` array:
```json
{
  "name": "NewModel",
  "years": {
    "2024": [{"trim": "Base", "engine": "2.0L I4", "turbo": false}],
    "2025": [{"trim": "Base", "engine": "2.0L I4", "turbo": false}]
  }
}
```

### Add New Years
Add years to the `years` array at the top:
```json
"years": [..., 2026, 2027]
```

### Add New Trims
Add trim objects to a model's year:
```json
"2024": [
  {"trim": "Base", "engine": "2.0L I4", "turbo": false},
  {"trim": "Sport", "engine": "2.5L I4", "turbo": true}
]
```

### Fix Existing Data
- Correct model names
- Fix engine specifications
- Update trim names
- Add missing years for models

## Version Numbering Best Practices

- **Start at 1** for your first version
- **Increment by 1** for each update
- **Don't skip numbers** (1, 2, 3, not 1, 5, 10)
- **Update version** even for small fixes

## Example Update

**Before:**
```json
{
  "version": 1,
  "years": [2020, 2021, 2022, 2023, 2024],
  "makes": [...]
}
```

**After adding 2025 and a new model:**
```json
{
  "version": 2,
  "years": [2020, 2021, 2022, 2023, 2024, 2025],
  "makes": [
    ...existing makes...,
    {
      "name": "NewBrand",
      "models": [
        {
          "name": "NewModel",
          "years": {
            "2025": [{"trim": "Base", "engine": "2.0L", "turbo": false}]
          }
        }
      ]
    }
  ]
}
```

## Testing Updates

1. Make your changes locally
2. Test the JSON is valid (use a JSON validator)
3. Commit and push to GitHub
4. Wait a few seconds for GitHub to update
5. Launch the app - you should see the update prompt!

## Important Notes

- ✅ Always increment the version number
- ✅ Keep JSON syntax valid (use a validator)
- ✅ Test locally before pushing
- ✅ The app checks for updates on every launch
- ✅ Users can choose to update or skip

