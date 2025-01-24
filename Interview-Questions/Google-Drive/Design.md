**Design a Cloud File Storage System (Google Drive/ Dropbox)**

Google Drive is a cloud file storage and synchronization service that helps you store documents, photos, videos, and other files in the cloud. You can access your files from any computer. The files can also be shared amongst friends and family.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------
**Phase-1: Requirement Gathering**

**Functional Requirements**

- Users can upload and download files from any device.
- Sync files across multiple devices.
- Share files with your friends, family, and coworkers.
- See file revisions

**Non-Functional Requirements**

- Low Latency uploads and downloads (in near real-time)
- Availability >> consistency
- Data reliability is of utmost importance.
- Fast sync

------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Back of the envelope estimation**

- 500M users of the system and 100M DAU
- Each user gets 10GB of Free Storage
- Total Storage Allocated: 50M * 10GB = 50,000,000 * 10 = 500,000,000GB = 500PB

------------------------------------------------------------------------------------------------------------------------------------------------------------------------

