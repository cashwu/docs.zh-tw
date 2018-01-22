---
uid: web-forms/overview/deployment/advanced-enterprise-web-deployment/advanced-enterprise-web-deployment
title: "進階企業 Web 部署 |Microsoft 文件"
author: jrjlee
description: "本教學課程會示範如何執行必要或適合在許多企業部署案例的各種工作。 義大利文的 translati for..."
ms.author: aspnetcontent
manager: wpickett
ms.date: 05/04/2012
ms.topic: article
ms.assetid: 7dcaba80-f2ec-4db3-ad98-daadc3afdb49
ms.technology: dotnet-webforms
ms.prod: .net-framework
msc.legacyurl: /web-forms/overview/deployment/advanced-enterprise-web-deployment/advanced-enterprise-web-deployment
msc.type: authoredcontent
ms.openlocfilehash: c3cb7f63cf7c0246a0c4da6038a65a6ac43a7b59
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2017
---
<a name="advanced-enterprise-web-deployment"></a><span data-ttu-id="54ee7-104">進階的企業 Web 部署</span><span class="sxs-lookup"><span data-stu-id="54ee7-104">Advanced Enterprise Web Deployment</span></span>
====================
<span data-ttu-id="54ee7-105">由[Jason Lee](https://github.com/jrjlee)</span><span class="sxs-lookup"><span data-stu-id="54ee7-105">by [Jason Lee](https://github.com/jrjlee)</span></span>

[<span data-ttu-id="54ee7-106">下載 PDF</span><span class="sxs-lookup"><span data-stu-id="54ee7-106">Download PDF</span></span>](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/63/56/8130.DeployingWebAppsInEnterpriseScenarios.pdf)

> <span data-ttu-id="54ee7-107">本教學課程會示範如何執行必要或適合在許多企業部署案例的各種工作。</span><span class="sxs-lookup"><span data-stu-id="54ee7-107">This tutorial will show you how to perform various tasks that are required or desirable in a lot of enterprise deployment scenarios.</span></span>
> 
> <span data-ttu-id="54ee7-108">這些教學課程的義大利文的翻譯，請瀏覽[http://www.lucamorelli.it](http://www.lucamorelli.it)。</span><span class="sxs-lookup"><span data-stu-id="54ee7-108">For an Italian translation of these tutorials, visit [http://www.lucamorelli.it](http://www.lucamorelli.it).</span></span>


<span data-ttu-id="54ee7-109">這會形成一系列以名為 Fabrikam，Inc.的虛構公司的企業部署需求基礎的教學課程的一部分此教學課程使用範例方案 & #x 2014;[連絡人管理員](../web-deployment-in-the-enterprise/the-contact-manager-solution.md)方案 & #x 2014; 代表實際的層級的複雜性，包括 ASP.NET MVC 3 應用程式時，Windows 與 web 應用程式Communication Foundation (WCF) 服務，與資料庫專案。</span><span class="sxs-lookup"><span data-stu-id="54ee7-109">This forms part of a series of tutorials based around the enterprise deployment requirements of a fictional company named Fabrikam, Inc. This tutorial series uses a sample solution&#x2014;the [Contact Manager](../web-deployment-in-the-enterprise/the-contact-manager-solution.md) solution&#x2014;to represent a web application with a realistic level of complexity, including an ASP.NET MVC 3 application, a Windows Communication Foundation (WCF) service, and a database project.</span></span>

<span data-ttu-id="54ee7-110">這些教學課程的核心的部署方法為基礎分割專案檔案描述的方法中[瞭解建置程序](../web-deployment-in-the-enterprise/understanding-the-build-process.md)，這在建置程序由兩個專案中檔案 & #x 2014; 一個包含建置適用於每個目的地環境中和包含特定環境的建置和部署設定的指示。</span><span class="sxs-lookup"><span data-stu-id="54ee7-110">The deployment method at the heart of these tutorials is based on the split project file approach described in [Understanding the Build Process](../web-deployment-in-the-enterprise/understanding-the-build-process.md), in which the build process is controlled by two project files&#x2014;one containing build instructions that apply to every destination environment, and one containing environment-specific build and deployment settings.</span></span> <span data-ttu-id="54ee7-111">在建置時，環境特定專案檔就會合併環境無從驗證專案檔來形成一組完整組建指示。</span><span class="sxs-lookup"><span data-stu-id="54ee7-111">At build time, the environment-specific project file is merged into the environment-agnostic project file to form a complete set of build instructions.</span></span>

## <a name="scenario-overview"></a><span data-ttu-id="54ee7-112">情節概觀</span><span class="sxs-lookup"><span data-stu-id="54ee7-112">Scenario Overview</span></span>

<span data-ttu-id="54ee7-113">這些教學課程的高層級案例所述[企業 Web 部署： 案例概觀](../deploying-web-applications-in-enterprise-scenarios/enterprise-web-deployment-scenario-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="54ee7-113">The high-level scenario for these tutorials is described in [Enterprise Web Deployment: Scenario Overview](../deploying-web-applications-in-enterprise-scenarios/enterprise-web-deployment-scenario-overview.md).</span></span> <span data-ttu-id="54ee7-114">我們建議您檢閱本主題，在開始此教學課程之前。</span><span class="sxs-lookup"><span data-stu-id="54ee7-114">We recommend that you review this topic before you get started on this tutorial.</span></span>

## <a name="how-to-use-this-tutorial"></a><span data-ttu-id="54ee7-115">如何使用本教學課程</span><span class="sxs-lookup"><span data-stu-id="54ee7-115">How to Use This Tutorial</span></span>

- <span data-ttu-id="54ee7-116">每個在本教學課程中的主題是獨立的並且將特定的挑戰或在企業部署案例中，就會發生的問題。</span><span class="sxs-lookup"><span data-stu-id="54ee7-116">Each of the topics in this tutorial is self-contained and addresses a particular challenge or problem that occurs in enterprise deployment scenarios.</span></span> <span data-ttu-id="54ee7-117">您不需要進行任何特定順序中的下列主題。</span><span class="sxs-lookup"><span data-stu-id="54ee7-117">You don't need to work through these topics in any particular order.</span></span> <span data-ttu-id="54ee7-118">不過，本教學課程涵蓋一些進階的工作。</span><span class="sxs-lookup"><span data-stu-id="54ee7-118">However, this tutorial covers some advanced tasks.</span></span> <span data-ttu-id="54ee7-119">因此，您應該熟悉的概念和技術，[企業中的 Web 部署](../web-deployment-in-the-enterprise/web-deployment-in-the-enterprise.md)教學課程涵蓋為了要能夠從這個內容的最大好處。</span><span class="sxs-lookup"><span data-stu-id="54ee7-119">As such, you should familiarize yourself with the concepts and techniques that the [Web Deployment in the Enterprise](../web-deployment-in-the-enterprise/web-deployment-in-the-enterprise.md) tutorial covers in order to gain the most benefit from this content.</span></span>
- <span data-ttu-id="54ee7-120">本教學課程包含下列主題：</span><span class="sxs-lookup"><span data-stu-id="54ee7-120">This tutorial includes these topics:</span></span>
- <span data-ttu-id="54ee7-121">[執行部署"What If"](performing-a-what-if-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="54ee7-121">[Performing a "What If" Deployment](performing-a-what-if-deployment.md).</span></span> <span data-ttu-id="54ee7-122">在許多案例中，您需要在實際進行任何變更之前，判斷建議的部署目標環境或任何現有的內容上的影響。</span><span class="sxs-lookup"><span data-stu-id="54ee7-122">In a lot of scenarios, you'll want to determine the impact of a proposed deployment on a target environment or any existing content before you actually make any changes.</span></span> <span data-ttu-id="54ee7-123">本主題說明如何執行 「 假設 」 部署以產生記錄檔和資料庫更新指令碼，就像您部署的內容至目標環境，而不實際進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="54ee7-123">This topic describes how you can run a "what if" deployment to generate log files and database update scripts as if you had deployed content to a target environment, without actually making any changes.</span></span> <span data-ttu-id="54ee7-124">分析這些資源可協助您找出任何可能的問題即時部署之前。</span><span class="sxs-lookup"><span data-stu-id="54ee7-124">Analyzing these resources can help you to spot any potential problems in advance of a live deployment.</span></span>
- <span data-ttu-id="54ee7-125">[自訂資料庫部署多個環境](customizing-database-deployments-for-multiple-environments.md)。</span><span class="sxs-lookup"><span data-stu-id="54ee7-125">[Customizing Database Deployments for Multiple Environments](customizing-database-deployments-for-multiple-environments.md).</span></span> <span data-ttu-id="54ee7-126">當您將資料庫專案部署到多個目的地時，您通常需要自訂每個目標環境的部署屬性。</span><span class="sxs-lookup"><span data-stu-id="54ee7-126">When you deploy a database project to multiple destinations, you'll often want to customize the deployment properties for each target environment.</span></span> <span data-ttu-id="54ee7-127">例如，在測試環境中您會通常重新建立資料庫上每個部署，而在預備或生產環境中您可能遠超過進行累加式更新，才能保留您的資料。</span><span class="sxs-lookup"><span data-stu-id="54ee7-127">For example, in test environments you'd typically recreate the database on every deployment, whereas in staging or production environments you'd be a lot more likely to make incremental updates to preserve your data.</span></span> <span data-ttu-id="54ee7-128">本主題描述如何建立每個目標環境的環境特定部署組態 (.sqldeployment) 檔案到您的部署邏輯加入這些屬性變更。</span><span class="sxs-lookup"><span data-stu-id="54ee7-128">This topic describes how you can incorporate these property changes into your deployment logic by creating an environment-specific deployment configuration (.sqldeployment) file for each target environment.</span></span>
- <span data-ttu-id="54ee7-129">將資料庫角色成員資格部署到測試環境。</span><span class="sxs-lookup"><span data-stu-id="54ee7-129">Deploying Database Role Memberships to Test Environments.</span></span> <span data-ttu-id="54ee7-130">當您重新建立資料庫，在每個部署 & #x 2014年; 例如，持續整合 (CI) 組建的一部分，並將部署到測試環境 & #x 2014; 通常會需要每次設定資料庫角色成員資格。</span><span class="sxs-lookup"><span data-stu-id="54ee7-130">When you recreate a database on every deployment&#x2014;for example, as part of a continuous integration (CI) build and deploy to a test environment&#x2014;you'll typically need to configure database role memberships every time.</span></span> <span data-ttu-id="54ee7-131">例如，您通常必須與您的 web 應用程式相關聯的應用程式集區識別的權限授與。</span><span class="sxs-lookup"><span data-stu-id="54ee7-131">For example, you'll usually need to grant permissions to the application pool identity associated with your web application.</span></span> <span data-ttu-id="54ee7-132">本主題描述如何將部署後 SQL 指令碼加入至您的部署邏輯可以自動化此程序。</span><span class="sxs-lookup"><span data-stu-id="54ee7-132">This topic describes how you can automate this process by adding a post-deployment SQL script to your deployment logic.</span></span>
- <span data-ttu-id="54ee7-133">[將成員資格資料庫部署至企業環境](deploying-membership-databases-to-enterprise-environments.md)。</span><span class="sxs-lookup"><span data-stu-id="54ee7-133">[Deploying Membership Databases to Enterprise Environments](deploying-membership-databases-to-enterprise-environments.md).</span></span> <span data-ttu-id="54ee7-134">ASP.NET 成員資格資料庫有可以使得在部署程序的各種特性。</span><span class="sxs-lookup"><span data-stu-id="54ee7-134">ASP.NET membership databases have various characteristics that can complicate the deployment process.</span></span> <span data-ttu-id="54ee7-135">例如，僅限結構描述的部署會讓資料庫處於非運作狀態。</span><span class="sxs-lookup"><span data-stu-id="54ee7-135">For example, a schema-only deployment will leave the database in a non-operational state.</span></span> <span data-ttu-id="54ee7-136">在大部分情況下，最好是直接在每個目的地環境中建立成員資格資料庫。</span><span class="sxs-lookup"><span data-stu-id="54ee7-136">In most scenarios, it's preferable to create a membership database directly in each destination environment.</span></span> <span data-ttu-id="54ee7-137">不過，如果您沒有將成員資格資料庫部署，本主題描述的一些方法，您可以用來滿足固有的挑戰。</span><span class="sxs-lookup"><span data-stu-id="54ee7-137">However, if you do have to deploy a membership database, this topic describes some of the approaches you can use to meet the inherent challenges.</span></span>
- <span data-ttu-id="54ee7-138">[從部署中排除檔案和資料夾](excluding-files-and-folders-from-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="54ee7-138">[Excluding Files and Folders from Deployment](excluding-files-and-folders-from-deployment.md).</span></span> <span data-ttu-id="54ee7-139">在某些情況下，您需要修改 web 套件到特定目的地環境的內容。</span><span class="sxs-lookup"><span data-stu-id="54ee7-139">In some scenarios, you'll want to tailor the contents of your web package to specific destination environments.</span></span> <span data-ttu-id="54ee7-140">比方說，您可能想要包含 JavaScript 程式庫的完整版本，當您將部署到測試環境中，以支援用戶端偵錯，但使用縮短的版本的程式庫，當您將部署至預備或生產環境。</span><span class="sxs-lookup"><span data-stu-id="54ee7-140">For example, you might want to include full versions of JavaScript libraries when you deploy to a test environment, to support client-side debugging, but use minified versions of the libraries when you deploy to a staging or production environment.</span></span> <span data-ttu-id="54ee7-141">本主題說明如何排除特定檔案和資料夾從封裝建立處理序。</span><span class="sxs-lookup"><span data-stu-id="54ee7-141">This topic describes how you can exclude specific files and folders from the package creation process.</span></span>
- <span data-ttu-id="54ee7-142">[函式使用 Web 應用程式離線 Web 部署](taking-web-applications-offline-with-web-deploy.md)。</span><span class="sxs-lookup"><span data-stu-id="54ee7-142">[Taking Web Applications Offline with Web Deploy](taking-web-applications-offline-with-web-deploy.md).</span></span> <span data-ttu-id="54ee7-143">當您將方案部署至預備或生產環境時，您通常需要部署程序期間需要 web 應用程式離線。</span><span class="sxs-lookup"><span data-stu-id="54ee7-143">When you deploy solutions to a staging or production environment, you'll often want to take your web applications offline for the duration of the deployment process.</span></span> <span data-ttu-id="54ee7-144">本主題描述如何新增*應用程式\_offline.htm* web 應用程式在開始部署程序的檔案，並在結束時將其移除。</span><span class="sxs-lookup"><span data-stu-id="54ee7-144">This topic describes how you can add an *App\_offline.htm* file to your web application at the start of the deployment process and remove it at the end.</span></span> <span data-ttu-id="54ee7-145">雖然*應用程式\_offline.htm*檔案位置中，瀏覽至 web 應用程式的使用者會自動重新導向至*應用程式\_offline.htm*檔案。</span><span class="sxs-lookup"><span data-stu-id="54ee7-145">While the *App\_offline.htm* file is in place, any users who browse to the web application are automatically redirected to the *App\_offline.htm* file.</span></span>
- <span data-ttu-id="54ee7-146">[執行 Windows PowerShell 指令碼從 MSBuild](running-windows-powershell-scripts-from-msbuild-project-files.md)。</span><span class="sxs-lookup"><span data-stu-id="54ee7-146">[Running Windows PowerShell Scripts from MSBuild](running-windows-powershell-scripts-from-msbuild-project-files.md).</span></span> <span data-ttu-id="54ee7-147">許多部署案例會需要更複雜的部署後動作，例如新增至登錄的自訂事件來源，或設定 SQL Server 執行個體之間的複寫。</span><span class="sxs-lookup"><span data-stu-id="54ee7-147">Many deployment scenarios require more complex post-deployment actions, like adding custom event sources to the registry or configuring replication between SQL Server instances.</span></span> <span data-ttu-id="54ee7-148">這些動作通常是透過 Windows PowerShell 指令碼完成。</span><span class="sxs-lookup"><span data-stu-id="54ee7-148">These actions are often accomplished through Windows PowerShell scripts.</span></span> <span data-ttu-id="54ee7-149">本主題描述如何從 Microsoft Build Engine (MSBuild) 專案檔中執行 Windows PowerShell 指令碼，做為建置和部署處理程序的一部分。</span><span class="sxs-lookup"><span data-stu-id="54ee7-149">This topic describes how to run Windows PowerShell scripts from a Microsoft Build Engine (MSBuild) project file as part of the build and deployment process.</span></span>
- <span data-ttu-id="54ee7-150">[疑難排解封裝程序](troubleshooting-the-packaging-process.md)。</span><span class="sxs-lookup"><span data-stu-id="54ee7-150">[Troubleshooting the Packaging Process](troubleshooting-the-packaging-process.md).</span></span> <span data-ttu-id="54ee7-151">Web 發行管線 (WPP) 會定義名為 MSBuild 屬性**EnablePackageProcessLoggingAndAssert**可用來產生 web 應用程式專案的封裝程序的深入資訊。</span><span class="sxs-lookup"><span data-stu-id="54ee7-151">The Web Publishing Pipeline (WPP) defines an MSBuild property named **EnablePackageProcessLoggingAndAssert** that you can use to generate in-depth information about the packaging process for web application projects.</span></span> <span data-ttu-id="54ee7-152">本主題描述之屬性的用途以及如何使用它。</span><span class="sxs-lookup"><span data-stu-id="54ee7-152">This topic describes what the property does and how to use it.</span></span>

## <a name="key-technologies"></a><span data-ttu-id="54ee7-153">關鍵技術</span><span class="sxs-lookup"><span data-stu-id="54ee7-153">Key Technologies</span></span>

<span data-ttu-id="54ee7-154">本教學課程著重於如何使用這些產品和技術支援自動化的建置和 web 部署：</span><span class="sxs-lookup"><span data-stu-id="54ee7-154">This tutorial focuses on how to use these products and technologies to support automated build and web deployment:</span></span>

- <span data-ttu-id="54ee7-155">Visual Studio 2010 和 Team Foundation Server (TFS) 2010</span><span class="sxs-lookup"><span data-stu-id="54ee7-155">Visual Studio 2010 and Team Foundation Server (TFS) 2010</span></span>
- <span data-ttu-id="54ee7-156">MSBuild 和 TFS Team Build</span><span class="sxs-lookup"><span data-stu-id="54ee7-156">MSBuild and TFS Team Build</span></span>
- <span data-ttu-id="54ee7-157">Internet Information Services (IIS) 7.5</span><span class="sxs-lookup"><span data-stu-id="54ee7-157">Internet Information Services (IIS) 7.5</span></span>
- <span data-ttu-id="54ee7-158">IIS Web Deployment Tool (Web Deploy) 2.1</span><span class="sxs-lookup"><span data-stu-id="54ee7-158">IIS Web Deployment Tool (Web Deploy) 2.1</span></span>
- <span data-ttu-id="54ee7-159">VSDBCMD.exe 資料庫部署公用程式</span><span class="sxs-lookup"><span data-stu-id="54ee7-159">The VSDBCMD.exe database deployment utility</span></span>

## <a name="other-tutorials-in-this-series"></a><span data-ttu-id="54ee7-160">在這一系列其他教學課程</span><span class="sxs-lookup"><span data-stu-id="54ee7-160">Other Tutorials in This Series</span></span>

<span data-ttu-id="54ee7-161">這會形成企業規模的 web 部署的一系列的五個教學課程的一部分。</span><span class="sxs-lookup"><span data-stu-id="54ee7-161">This forms part of a series of five tutorials on enterprise-scale web deployment.</span></span> <span data-ttu-id="54ee7-162">這些是數列中的其他教學課程：</span><span class="sxs-lookup"><span data-stu-id="54ee7-162">These are other tutorials in the series:</span></span>

- <span data-ttu-id="54ee7-163">[部署企業案例中的 Web 應用程式](../deploying-web-applications-in-enterprise-scenarios/deploying-web-applications-in-enterprise-scenarios.md)。</span><span class="sxs-lookup"><span data-stu-id="54ee7-163">[Deploying Web Applications in Enterprise Scenarios](../deploying-web-applications-in-enterprise-scenarios/deploying-web-applications-in-enterprise-scenarios.md).</span></span> <span data-ttu-id="54ee7-164">此入門內容提供教學課程系列內容的背景。</span><span class="sxs-lookup"><span data-stu-id="54ee7-164">This introductory content provides the contextual background for the tutorial series.</span></span> <span data-ttu-id="54ee7-165">它描述教學課程案例中，並將說明如何工作與數列中所描述的逐步解說納入更廣泛的應用程式生命週期管理 (ALM) 程序。</span><span class="sxs-lookup"><span data-stu-id="54ee7-165">It describes the tutorial scenario, and it illustrates how the tasks and walkthroughs described throughout the series fit into a broader Application Lifecycle Management (ALM) process.</span></span>
- <span data-ttu-id="54ee7-166">[Web 部署，在企業中的](../web-deployment-in-the-enterprise/web-deployment-in-the-enterprise.md)。</span><span class="sxs-lookup"><span data-stu-id="54ee7-166">[Web Deployment in the Enterprise](../web-deployment-in-the-enterprise/web-deployment-in-the-enterprise.md).</span></span> <span data-ttu-id="54ee7-167">本教學課程提供 MSBuild 專案檔的概念性簡介、 WPP、 Web Deploy，和其他相關的技術。</span><span class="sxs-lookup"><span data-stu-id="54ee7-167">This tutorial provides a conceptual introduction to MSBuild project files, the WPP, Web Deploy, and other related technologies.</span></span> <span data-ttu-id="54ee7-168">它說明如何使用這些工具一起管理複雜的部署處理程序。</span><span class="sxs-lookup"><span data-stu-id="54ee7-168">It explains how you can use these tools together to manage complex deployment processes.</span></span>
- <span data-ttu-id="54ee7-169">[用於 Web 部署設定伺服器環境](../configuring-server-environments-for-web-deployment/configuring-server-environments-for-web-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="54ee7-169">[Configuring Server Environments for Web Deployment](../configuring-server-environments-for-web-deployment/configuring-server-environments-for-web-deployment.md).</span></span> <span data-ttu-id="54ee7-170">本教學課程說明如何設定 Windows servers 以支援各種部署案例，包括使用 Web Deployment Agent Service （遠端代理程式） 或 Web 部署的處理常式和遠端資料庫部署的遠端 web 封裝部署。</span><span class="sxs-lookup"><span data-stu-id="54ee7-170">This tutorial describes how to configure Windows servers to support various deployment scenarios, including remote web package deployment using the Web Deployment Agent Service (the remote agent) or the Web Deploy Handler and remote database deployment.</span></span> <span data-ttu-id="54ee7-171">它提供有關選擇您自己的環境中，適當的部署方法的指引，並說明如何使用伺服器陣列中的所有 web 伺服器之間複寫部署的 web 應用程式的 Web 伺服陣列架構 (WFF)。</span><span class="sxs-lookup"><span data-stu-id="54ee7-171">It provides guidance on choosing the appropriate deployment method for your own environment, and it describes how to use the Web Farm Framework (WFF) to replicate deployed web applications across all the web servers in a server farm.</span></span>
- <span data-ttu-id="54ee7-172">[設定用於 Web 部署的 Team Foundation Server](../configuring-team-foundation-server-for-web-deployment/configuring-team-foundation-server-for-web-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="54ee7-172">[Configuring Team Foundation Server for Web Deployment](../configuring-team-foundation-server-for-web-deployment/configuring-team-foundation-server-for-web-deployment.md).</span></span> <span data-ttu-id="54ee7-173">本教學課程說明如何設定 TFS 以支援各種部署案例，包括自動化的部署 CI 程序的一部分，以及手動觸發部署的特定組建。</span><span class="sxs-lookup"><span data-stu-id="54ee7-173">This tutorial describes how to configure TFS to support various deployment scenarios, including automated deployment as part of a CI process and manually triggered deployments of specific builds.</span></span>

>[!div class="step-by-step"]
[<span data-ttu-id="54ee7-174">下一步</span><span class="sxs-lookup"><span data-stu-id="54ee7-174">Next</span></span>](performing-a-what-if-deployment.md)