---
title: 'NETSDK1145: destino ou pacote de appHost ausente'
description: Como resolver o problema do pacote de direcionamento ausente enquanto a restauração do pacote NuGet não é suportada
author: wli3
ms.topic: error-reference
ms.date: 09/14/2020
f1_keywords:
- NETSDK1145
ms.openlocfilehash: c343952582cafb63eae388fd216769e6c67d4741
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91805317"
---
# <a name="netsdk1145-targeting-or-apphost-pack-missing"></a><span data-ttu-id="a3365-103">NETSDK1145: destino ou pacote de appHost ausente</span><span class="sxs-lookup"><span data-stu-id="a3365-103">NETSDK1145: Targeting or apphost pack missing</span></span>

<span data-ttu-id="a3365-104">**Este artigo aplica-se a:** ✔️ o SDK do .NET 5.0.100 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="a3365-104">**This article applies to:** ✔️ .NET 5.0.100 SDK and later versions</span></span>

<span data-ttu-id="a3365-105">Quando o SDK do .NET emite o erro NETSDK1145, o pacote de destino ou appHost não está instalado e não há suporte para a restauração do pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="a3365-105">When the .NET SDK issues error NETSDK1145, the targeting or apphost pack is not installed and NuGet package restore is not supported.</span></span> <span data-ttu-id="a3365-106">Isso geralmente é causado por ter um SDK mais recente do que aquele incluído no Visual Studio para projetos C++/CLI.</span><span class="sxs-lookup"><span data-stu-id="a3365-106">This is typically caused by having a newer SDK than the one included in Visual Studio for C++/CLI projects.</span></span> <span data-ttu-id="a3365-107">Atualize o Visual Studio, remova _global.js_ se ele especificar uma determinada versão do SDK e desinstale o SDK mais recente.</span><span class="sxs-lookup"><span data-stu-id="a3365-107">Upgrade Visual Studio, remove _global.json_ if it specifies a certain SDK version, and uninstall the newer SDK.</span></span> <span data-ttu-id="a3365-108">Como alternativa, você pode substituir a versão de destino ou appHost.</span><span class="sxs-lookup"><span data-stu-id="a3365-108">Alternatively, you could override the targeting or apphost version.</span></span> <span data-ttu-id="a3365-109">Localize a versão que existe no diretório do pacote a partir da mensagem de erro e corresponde à estrutura de destino do projeto.</span><span class="sxs-lookup"><span data-stu-id="a3365-109">Find the version that exists under the pack directory from the error message and matches the target framework of the project.</span></span> <span data-ttu-id="a3365-110">Adicione o seguinte ao projeto:</span><span class="sxs-lookup"><span data-stu-id="a3365-110">Add the following to the project:</span></span>

<span data-ttu-id="a3365-111">Para APPHOST Pack</span><span class="sxs-lookup"><span data-stu-id="a3365-111">For apphost pack</span></span>

```xml
<ItemGroup>
  <KnownAppHostPack Update="@(KnownAppHostPack)">
    <AppHostPackVersion Condition="'%(TargetFramework)' == 'TARGETFRAMEWORK'">EXISTINGVERSION</AppHostPackVersion>
  </KnownAppHostPack>
</ItemGroup>
```

<span data-ttu-id="a3365-112">Para o pacote de direcionamento</span><span class="sxs-lookup"><span data-stu-id="a3365-112">For targeting pack</span></span>

```xml
<ItemGroup>
  <KnownAppHostPack Update="@(KnownAppHostPack)">
    <AppHostPackVersion Condition="'%(TargetFramework)' == 'TARGETFRAMEWORK'">EXISTINGVERSION</AppHostPackVersion>
  </KnownAppHostPack>
</ItemGroup>
```
