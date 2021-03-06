﻿USE [WaDE_Oct2014]
GO

/****** Object:  Table [wade].[SUMMARY_USE]    Script Date: 8/15/2016 10:55:43 AM ******/
SET ANSI_NULLS ON
GO

SET QUOTED_IDENTIFIER ON
GO

SET ANSI_PADDING ON
GO

CREATE TABLE [wade].[SUMMARY_USE](
	[ORGANIZATION_ID] [varchar](10) NOT NULL,
	[REPORT_ID] [varchar](35) NOT NULL,
	[REPORT_UNIT_ID] [varchar](35) NOT NULL,
	[SUMMARY_SEQ] [numeric](18, 0) NOT NULL,
	[BENEFICIAL_USE_ID] [numeric](18, 0) NOT NULL,
	[FRESH_SALINE_IND] [numeric](18, 0) NOT NULL,
	[SOURCE_TYPE] [numeric](18, 0) NOT NULL,
	[POWER_GENERATED] [numeric](18, 3) NULL,
	[POPULATION_SERVED] [numeric](18, 3) NULL,
	[WFS_FEATURE_REF] [varchar](35) NULL,
 CONSTRAINT [PK_SUMMARY_USE] PRIMARY KEY CLUSTERED 
(
	[ORGANIZATION_ID] ASC,
	[REPORT_ID] ASC,
	[REPORT_UNIT_ID] ASC,
	[SUMMARY_SEQ] ASC,
	[BENEFICIAL_USE_ID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]

GO

SET ANSI_PADDING OFF
GO

ALTER TABLE [wade].[SUMMARY_USE]  WITH CHECK ADD  CONSTRAINT [FK_SUMMARY_USE_LU_BENEFICIAL_USE] FOREIGN KEY([BENEFICIAL_USE_ID])
REFERENCES [wade].[LU_BENEFICIAL_USE] ([LU_SEQ_NO])
ON UPDATE CASCADE
GO

ALTER TABLE [wade].[SUMMARY_USE] CHECK CONSTRAINT [FK_SUMMARY_USE_LU_BENEFICIAL_USE]
GO

ALTER TABLE [wade].[SUMMARY_USE]  WITH CHECK ADD  CONSTRAINT [FK_SUMMARY_USE_LU_FRESH_SALINE_INDICATOR] FOREIGN KEY([FRESH_SALINE_IND])
REFERENCES [wade].[LU_FRESH_SALINE_INDICATOR] ([LU_SEQ_NO])
ON UPDATE CASCADE
GO

ALTER TABLE [wade].[SUMMARY_USE] CHECK CONSTRAINT [FK_SUMMARY_USE_LU_FRESH_SALINE_INDICATOR]
GO

ALTER TABLE [wade].[SUMMARY_USE]  WITH CHECK ADD  CONSTRAINT [FK_SUMMARY_USE_LU_SOURCE_TYPE] FOREIGN KEY([SOURCE_TYPE])
REFERENCES [wade].[LU_SOURCE_TYPE] ([LU_SEQ_NO])
ON UPDATE CASCADE
GO

ALTER TABLE [wade].[SUMMARY_USE] CHECK CONSTRAINT [FK_SUMMARY_USE_LU_SOURCE_TYPE]
GO

ALTER TABLE [wade].[SUMMARY_USE]  WITH NOCHECK ADD  CONSTRAINT [FK_SUMMARY_USE_REPORTING_UNIT] FOREIGN KEY([ORGANIZATION_ID], [REPORT_ID], [REPORT_UNIT_ID])
REFERENCES [wade].[REPORTING_UNIT] ([ORGANIZATION_ID], [REPORT_ID], [REPORT_UNIT_ID])
ON UPDATE CASCADE
ON DELETE CASCADE
GO

ALTER TABLE [wade].[SUMMARY_USE] CHECK CONSTRAINT [FK_SUMMARY_USE_REPORTING_UNIT]
GO

EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'Unique identifier assigned to the organization.' , @level0type=N'SCHEMA',@level0name=N'wade', @level1type=N'TABLE',@level1name=N'SUMMARY_USE', @level2type=N'COLUMN',@level2name=N'ORGANIZATION_ID'
GO

EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'A unique identifier assigned to the report by the organization.' , @level0type=N'SCHEMA',@level0name=N'wade', @level1type=N'TABLE',@level1name=N'SUMMARY_USE', @level2type=N'COLUMN',@level2name=N'REPORT_ID'
GO

EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'A unique identifier assigned to the reporting unit by the organization.' , @level0type=N'SCHEMA',@level0name=N'wade', @level1type=N'TABLE',@level1name=N'SUMMARY_USE', @level2type=N'COLUMN',@level2name=N'REPORT_UNIT_ID'
GO

EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'A unique identifier for the use summary.' , @level0type=N'SCHEMA',@level0name=N'wade', @level1type=N'TABLE',@level1name=N'SUMMARY_USE', @level2type=N'COLUMN',@level2name=N'SUMMARY_SEQ'
GO

EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'Unique identifier for the beneficial use.' , @level0type=N'SCHEMA',@level0name=N'wade', @level1type=N'TABLE',@level1name=N'SUMMARY_USE', @level2type=N'COLUMN',@level2name=N'BENEFICIAL_USE_ID'
GO


