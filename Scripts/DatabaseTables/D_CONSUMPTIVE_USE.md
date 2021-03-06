﻿USE [WaDE_Oct2014]
GO

/****** Object:  Table [wade].[D_CONSUMPTIVE_USE]    Script Date: 8/15/2016 10:09:59 AM ******/
SET ANSI_NULLS ON
GO

SET QUOTED_IDENTIFIER ON
GO

SET ANSI_PADDING ON
GO

CREATE TABLE [wade].[D_CONSUMPTIVE_USE](
	[ORGANIZATION_ID] [varchar](10) NOT NULL,
	[REPORT_ID] [varchar](35) NOT NULL,
	[ALLOCATION_ID] [varchar](60) NOT NULL,
	[WATER_USER_ID] [varchar](50) NOT NULL,
	[BENEFICIAL_USE_ID] [numeric](18, 0) NOT NULL,
	[SOURCE_TYPE] [numeric](18, 0) NULL,
	[FRESH_SALINE_IND] [numeric](18, 0) NULL,
	[SOURCE_NAME] [varchar](60) NULL,
 CONSTRAINT [PK_D_CONSUMPTIVE_USE] PRIMARY KEY CLUSTERED 
(
	[ORGANIZATION_ID] ASC,
	[REPORT_ID] ASC,
	[ALLOCATION_ID] ASC,
	[WATER_USER_ID] ASC,
	[BENEFICIAL_USE_ID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]

GO

SET ANSI_PADDING OFF
GO

ALTER TABLE [wade].[D_CONSUMPTIVE_USE]  WITH CHECK ADD  CONSTRAINT [FK_D_CONSUMPTIVE_USE_DETAIL_USE] FOREIGN KEY([ORGANIZATION_ID], [REPORT_ID], [ALLOCATION_ID], [WATER_USER_ID])
REFERENCES [wade].[DETAIL_USE] ([ORGANIZATION_ID], [REPORT_ID], [ALLOCATION_ID], [WATER_USER_ID])
ON UPDATE CASCADE
GO

ALTER TABLE [wade].[D_CONSUMPTIVE_USE] CHECK CONSTRAINT [FK_D_CONSUMPTIVE_USE_DETAIL_USE]
GO

ALTER TABLE [wade].[D_CONSUMPTIVE_USE]  WITH CHECK ADD  CONSTRAINT [FK_D_CONSUMPTIVE_USE_LU_BENEFICIAL_USE] FOREIGN KEY([BENEFICIAL_USE_ID])
REFERENCES [wade].[LU_BENEFICIAL_USE] ([LU_SEQ_NO])
ON UPDATE CASCADE
GO

ALTER TABLE [wade].[D_CONSUMPTIVE_USE] CHECK CONSTRAINT [FK_D_CONSUMPTIVE_USE_LU_BENEFICIAL_USE]
GO

ALTER TABLE [wade].[D_CONSUMPTIVE_USE]  WITH CHECK ADD  CONSTRAINT [FK_D_CONSUMPTIVE_USE_LU_FRESH_SALINE_INDICATOR] FOREIGN KEY([FRESH_SALINE_IND])
REFERENCES [wade].[LU_FRESH_SALINE_INDICATOR] ([LU_SEQ_NO])
ON UPDATE CASCADE
GO

ALTER TABLE [wade].[D_CONSUMPTIVE_USE] CHECK CONSTRAINT [FK_D_CONSUMPTIVE_USE_LU_FRESH_SALINE_INDICATOR]
GO

ALTER TABLE [wade].[D_CONSUMPTIVE_USE]  WITH CHECK ADD  CONSTRAINT [FK_D_CONSUMPTIVE_USE_LU_SOURCE_TYPE] FOREIGN KEY([SOURCE_TYPE])
REFERENCES [wade].[LU_SOURCE_TYPE] ([LU_SEQ_NO])
ON UPDATE CASCADE
GO

ALTER TABLE [wade].[D_CONSUMPTIVE_USE] CHECK CONSTRAINT [FK_D_CONSUMPTIVE_USE_LU_SOURCE_TYPE]
GO

EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N' A unique identifier assigned to the organziation.' , @level0type=N'SCHEMA',@level0name=N'wade', @level1type=N'TABLE',@level1name=N'D_CONSUMPTIVE_USE', @level2type=N'COLUMN',@level2name=N'ORGANIZATION_ID'
GO

EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'A unique identifier assigned to the report by the reporting organziation.' , @level0type=N'SCHEMA',@level0name=N'wade', @level1type=N'TABLE',@level1name=N'D_CONSUMPTIVE_USE', @level2type=N'COLUMN',@level2name=N'REPORT_ID'
GO

EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'Unique identifier for the allocation.' , @level0type=N'SCHEMA',@level0name=N'wade', @level1type=N'TABLE',@level1name=N'D_CONSUMPTIVE_USE', @level2type=N'COLUMN',@level2name=N'ALLOCATION_ID'
GO

EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'A unique identifier for the water user.' , @level0type=N'SCHEMA',@level0name=N'wade', @level1type=N'TABLE',@level1name=N'D_CONSUMPTIVE_USE', @level2type=N'COLUMN',@level2name=N'WATER_USER_ID'
GO

EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'A unique identifier identifying the beneficial use.' , @level0type=N'SCHEMA',@level0name=N'wade', @level1type=N'TABLE',@level1name=N'D_CONSUMPTIVE_USE', @level2type=N'COLUMN',@level2name=N'BENEFICIAL_USE_ID'
GO