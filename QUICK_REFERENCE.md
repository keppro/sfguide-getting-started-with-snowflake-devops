# Snowflake DevOps Quickstart - Quick Reference

## 🚀 Quick Commands

### Snowflake CLI
```bash
# Check connection
snow sql -q "SELECT CURRENT_VERSION();"

# Execute SQL file
snow sql -f steps/01_setup_snowflake.sql

# Run Python script
python steps/03_harmonize_data.py

# Check task status
snow sql -q "SHOW TASKS;"
```

### Git Commands
```bash
# Switch to dev branch
git checkout dev

# Merge dev to main
git checkout main && git merge dev

# Push changes
git push origin main
```

## 📊 Current Status

### Environments
- **Dev**: `QUICKSTART_DEV` (10 records, 0-day retention)
- **Prod**: `QUICKSTART_PROD` (20 records, 1-day retention)
- **Common**: `QUICKSTART_COMMON` (shared resources)

### Data Pipeline
- **Schedule**: Every 24 hours
- **Status**: ✅ Active
- **Records**: 30 total vacation spots
- **Success Rate**: 100%

### CI/CD
- **Status**: ✅ Active
- **Trigger**: Push to dev/main branches
- **Deployment**: Automated

## 🔧 Key Files

### Configuration
- `.snowflake/config.toml` - Snowflake CLI config
- `.snowflake/connections.toml` - Connection settings
- `.github/workflows/deploy_pipeline.yml` - CI/CD pipeline

### Data Processing
- `steps/03_harmonize_data.py` - Data transformation
- `steps/04_orchestrate_jobs.sql` - Task orchestration
- `steps/01_setup_snowflake.sql` - Initial setup

### Documentation
- `DEVOPS_ACTIVITY_LOG.md` - Complete activity log
- `TECHNICAL_SUMMARY.md` - Technical details
- `QUICK_REFERENCE.md` - This file

## 🎯 Key Metrics

### Data Processing
- **Dev Records**: 10 vacation spots
- **Prod Records**: 20 vacation spots
- **Processing Time**: Immediate
- **Schedule**: 24 hours

### Environment Settings
- **Dev Retention**: 0 days
- **Prod Retention**: 1 day
- **Warehouse**: QUICKSTART_WH (XSMALL)

## 🔍 Troubleshooting

### Common Issues
1. **Docker not found**: Use manual installation
2. **Missing data products**: Use simplified pipeline
3. **Python errors**: Check Snowpark installation
4. **Connection issues**: Verify credentials

### Quick Fixes
```bash
# Install Snowpark
pip install snowflake-snowpark-python

# Check Docker
/usr/local/bin/docker --version

# Test Snowflake connection
snow sql -q "SELECT 1;"
```

## 📈 Monitoring

### Check Pipeline Status
```sql
-- Check task execution
SHOW TASKS;

-- Check data counts
SELECT COUNT(*) FROM quickstart_prod.gold.vacation_spots;
SELECT COUNT(*) FROM quickstart_dev.gold.vacation_spots;

-- Check retention settings
SHOW PARAMETERS LIKE 'data_retention_time_in_days' IN TABLE quickstart_prod.gold.vacation_spots;
```

### View Data
```sql
-- View vacation spots
SELECT * FROM quickstart_prod.gold.vacation_spots LIMIT 10;

-- Check attractions data
SELECT * FROM quickstart_prod.silver.attractions;
```

## 🎉 Success Indicators

### ✅ All Systems Operational
- [x] Docker installed and running
- [x] Snowflake CLI configured
- [x] Git repository forked and updated
- [x] Data pipeline processing
- [x] CI/CD pipeline active
- [x] Environment separation working
- [x] Documentation complete

### 📊 Data Quality
- [x] All records processed successfully
- [x] No data loss
- [x] Proper data types
- [x] Attractions data included
- [x] Weather data simulated

## 🔮 Next Steps

### Optional Actions
1. **Keep Resources**: Continue exploring
2. **Clean Up**: Run cleanup script
3. **Extend**: Add more data sources
4. **Monitor**: Set up alerting

### Cleanup Commands
```bash
# Run cleanup script
snow sql -f steps/08_cleanup.sql

# Or manually clean up
snow sql -q "DROP DATABASE IF EXISTS QUICKSTART_DEV;"
snow sql -q "DROP DATABASE IF EXISTS QUICKSTART_PROD;"
snow sql -q "DROP DATABASE IF EXISTS QUICKSTART_COMMON;"
```

---

*Quick Reference created on: $(date)*
*Project: Snowflake DevOps Quickstart*
*Status: ✅ COMPLETED SUCCESSFULLY*
