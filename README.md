GoogleDriveExample
====================================

GoogleDriveExample is an assembly/ library on how to work with the Google.Apis.Drive.v3.dll.
The assembly was written and tested in .Net 4.8.

[![Build status](https://ci.appveyor.com/api/projects/status/qmem8i9v5no63wfg?svg=true)](https://ci.appveyor.com/project/SeppPenner/googledriveexample)
[![GitHub issues](https://img.shields.io/github/issues/SeppPenner/GoogleDriveExample.svg)](https://github.com/SeppPenner/GoogleDriveExample/issues)
[![GitHub forks](https://img.shields.io/github/forks/SeppPenner/GoogleDriveExample.svg)](https://github.com/SeppPenner/GoogleDriveExample/network)
[![GitHub stars](https://img.shields.io/github/stars/SeppPenner/GoogleDriveExample.svg)](https://github.com/SeppPenner/GoogleDriveExample/stargazers)
[![GitHub license](https://img.shields.io/badge/license-AGPL-blue.svg)](https://raw.githubusercontent.com/SeppPenner/GoogleDriveExample/master/License.txt)
[![Known Vulnerabilities](https://snyk.io/test/github/SeppPenner/GoogleDriveExample/badge.svg)](https://snyk.io/test/github/SeppPenner/GoogleDriveExample)

## Basic usage:
```csharp
public void Test()
{
    ICustomGDriveService _service = new CustomGDriveService();
    _service.xy //See the interface section for more information
}
```

## Interface ICustomGDriveService
```csharp
using System;
using Google.Apis.Drive.v3;
using GoogleDriveExample.Implementation;

namespace GoogleDriveExample.Interfaces
{
    /// <summary>
    ///     The Google <see cref="CustomGDriveService" /> class
    /// </summary>
    public interface ICustomGDriveService
    {
        /// <summary>
        ///     Gets the used quota of the account
        /// </summary>
        /// <param name="service">The <see cref="DriveService" /> that is needed</param>
        /// <returns>The used quota of the account</returns>
        long GetQuotaUsed(DriveService service);

        /// <summary>
        ///     Gets the total quota (is 15 GB) of the account
        /// </summary>
        /// <param name="service">The <see cref="DriveService" /> that is needed</param>
        /// <returns>The total quota of the account</returns>
        long GetQuotaTotal(DriveService service);

        /// <summary>
        ///     Uploads a file to GDrive with "everone that has the link can read the file" rights
        /// </summary>
        /// <param name="service">The <see cref="DriveService" /> that is needed</param>
        /// <param name="uploadFile">The File that should be uploaded</param>
        /// <param name="parent">The parent folder</param>
        /// <returns>The download link to the file</returns>
        string UploadToGDrive(DriveService service, string uploadFile, string parent);

        /// <summary>
        ///     Gets the root folder id of the account
        /// </summary>
        /// <param name="service">The <see cref="DriveService" /> that is needed</param>
        /// <returns>The root folder id for the account</returns>
        string GetRootFolderId(DriveService service);

        /// <summary>
        ///     Gets the <see cref="DriveService" /> needed in the methods above
        /// </summary>
        /// <param name="clientId">The client id that needs to be set inside the Google account (API-Key)</param>
        /// <param name="clientSecret">The client secret/ password</param>
        /// <param name="userName">The client username</param>
        /// <returns>The <see cref="DriveService" /> needed to authenticate the above methods</returns>
        DriveService GetDriveService(string clientId, string clientSecret, string userName);

        /// <summary>
        ///     Called when the upload process is changed
        /// </summary>
        event EventHandler OnUploadProgessChanged;

        /// <summary>
        ///     Called when the upload process is finished
        /// </summary>
        event EventHandler OnUploadSuccessfull;
    }
}
```


Change history
--------------

* **Version 1.0.0.1 (2019-05-05)** : Updated .Net version to 4.8.
* **Version 1.0.0.0 (2017-05-15)** : 1.0 release.
