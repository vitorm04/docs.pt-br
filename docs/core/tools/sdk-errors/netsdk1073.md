---
title: 'NETSDK1073: o FrameworkReference não foi reconhecido'
description: Como resolver o problema em que o FrameworkReference não pode ser encontrado.
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1073
ms.openlocfilehash: 59b5f63dcfe0115feabc2d87d24a09c6a650cc62
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91957131"
---
# <a name="netsdk1073-the-frameworkreference-was-not-recognized"></a><span data-ttu-id="53b54-103">NETSDK1073: o FrameworkReference não foi reconhecido</span><span class="sxs-lookup"><span data-stu-id="53b54-103">NETSDK1073: The FrameworkReference was not recognized</span></span>

<span data-ttu-id="53b54-104">**Este artigo aplica-se a:** ✔️ o SDK do .NET 2.1.100 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="53b54-104">**This article applies to:** ✔️ .NET 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="53b54-105">Esse erro normalmente significa que há uma versão de um determinado FrameworkReference que o SDK não pode localizar.</span><span class="sxs-lookup"><span data-stu-id="53b54-105">This error typically means there is a version of a particular FrameworkReference that the SDK cannot find.</span></span> <span data-ttu-id="53b54-106">Tente excluir as pastas *obj* e *bin* e execute `dotnet restore` para baixar novamente os pacotes de direcionamento mais recentes.</span><span class="sxs-lookup"><span data-stu-id="53b54-106">Try deleting your *obj* and *bin* folders and running `dotnet restore` to redownload the latest targeting packs.</span></span>

<span data-ttu-id="53b54-107">Como alternativa, pode haver um problema com a instalação, portanto, verifique se você está nas versões mais recentes do .NET e do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="53b54-107">Alternatively, there could be an issue with your install, so ensure you're on the latest versions of .NET and Visual Studio</span></span>
