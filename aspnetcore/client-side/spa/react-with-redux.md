---
title: React-with-Redux 專案範本搭配 ASP.NET Core 使用
author: SteveSandersonMS
description: 了解如何開始使用 React with Redux 和 create-react-app 適用的 ASP.NET Core 單頁應用程式 (SPA) 專案範本。
monikerRange: '>= aspnetcore-2.0'
ms.author: scaddie
ms.custom: mvc
ms.date: 02/21/2018
uid: spa/react-with-redux
ms.openlocfilehash: dab3d20865250aae548bff4614e631dd7c73b46f
ms.sourcegitcommit: a1afd04758e663d7062a5bfa8a0d4dca38f42afc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/20/2018
ms.locfileid: "36291481"
---
# <a name="use-the-react-with-redux-project-template-with-aspnet-core"></a>React-with-Redux 專案範本搭配 ASP.NET Core 使用

::: moniker range="= aspnetcore-2.0"

> [!NOTE]
> 本文件與 ASP.NET Core 2.0 包含的 React-with-Redux 專案範本無關。 而是討論您可以手動更新的新版 React-with-Redux 範本。 ASP.NET Core 2.1 預設會包含此範本。

::: moniker-end

更新的 React-with-Redux 專案範本很適合用來設計 ASP.NET Core 應用程式，而且可利用 React、Redux 和 [create-react-app](https://github.com/facebookincubator/create-react-app) (CRA) 慣例來實作一個功能多樣的用戶端使用者介面 (UI)。

除了專案建立命令，所有與 React-with-Redux 範本有關的資訊，都與 React 範本相同。 若要建立這種專案類型，請執行 `dotnet new reactredux` 而不是 `dotnet new react`。 對於這兩個以 React 為基礎的範本，如需深入了解其通用功能，請參閱 [React 範本文件](xref:spa/react)。
