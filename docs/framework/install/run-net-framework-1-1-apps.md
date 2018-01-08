---
title: Executar aplicativos do .NET Framework 1.1 no Windows 8, Windows 8.1 ou Windows 10
ms.custom: 
ms.date: 05/26/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9d5b99390e62984b37b0d7267c40b1221f556f60
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a><span data-ttu-id="90db4-102">Executar aplicativos do .NET Framework 1.1 no Windows 8, Windows 8.1 ou Windows 10</span><span class="sxs-lookup"><span data-stu-id="90db4-102">Run .NET Framework 1.1 apps on Windows 8, Windows 8.1, or Windows 10</span></span>

<span data-ttu-id="90db4-103">O .NET Framework 1.1 não tem suporte nos sistemas operacionais [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)] ou Windows 10.</span><span class="sxs-lookup"><span data-stu-id="90db4-103">The .NET Framework 1.1 is not supported on the [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], or the Windows 10 operating systems.</span></span> <span data-ttu-id="90db4-104">Em alguns casos, o .NET Framework 1.1 é especificamente identificado conforme necessário para um aplicativo ser executado.</span><span class="sxs-lookup"><span data-stu-id="90db4-104">In some cases, the .NET Framework 1.1 is specifically identified as required for an app to run.</span></span> <span data-ttu-id="90db4-105">Nesses casos, você deve entrar em contato com seu ISV (fornecedor independente de software) para que o aplicativo fosse atualizado para execução no [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] ou em uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="90db4-105">In those cases, you should contact your independent software vendor (ISV) to have the app upgraded to run on the [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] or later version.</span></span> <span data-ttu-id="90db4-106">Para saber mais, confira [Migrar do .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).</span><span class="sxs-lookup"><span data-stu-id="90db4-106">For additional information, see [Migrating from the .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).</span></span>

## <a name="install-the-net-framework-11-from-a-cd-or-download-center"></a><span data-ttu-id="90db4-107">Instalar o .NET Framework 1.1 de um CD ou do Centro de Download</span><span class="sxs-lookup"><span data-stu-id="90db4-107">Install the .NET Framework 1.1 from a CD or Download Center</span></span>

<span data-ttu-id="90db4-108">Não é possível instalar manualmente o .NET Framework 1.1 no [!INCLUDE[win8](../../../includes/win8-md.md)], no [!INCLUDE[win81](../../../includes/win81-md.md)], no [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], no [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)] ou no Windows 10.</span><span class="sxs-lookup"><span data-stu-id="90db4-108">It isn't possible to manually install the .NET Framework 1.1 on [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], or Windows 10.</span></span> <span data-ttu-id="90db4-109">Ele não é mais compatível.</span><span class="sxs-lookup"><span data-stu-id="90db4-109">It is no longer supported.</span></span> <span data-ttu-id="90db4-110">Se você tentar instalar o pacote, a seguinte mensagem de erro será exibida: "A instalação não pode continuar porque esta versão do .NET Framework é incompatível com a instalada anteriormente."</span><span class="sxs-lookup"><span data-stu-id="90db4-110">If you try to install the package, the following error message is displayed: "Setup cannot continue because this version of the .NET Framework is incompatible with a previously installed one."</span></span> <span data-ttu-id="90db4-111">Para resolver esse problema, instale o [.NET Framework 3.5 SP1](http://www.microsoft.com/download/details.aspx?id=22).</span><span class="sxs-lookup"><span data-stu-id="90db4-111">To solve this problem, install the [.NET Framework 3.5 SP1](http://www.microsoft.com/download/details.aspx?id=22).</span></span> <span data-ttu-id="90db4-112">Essa versão inclui o .NET Framework 2.0 (a versão após o .NET Framework 1.1), que tem suporte no [!INCLUDE[win8](../../../includes/win8-md.md)], no [!INCLUDE[win81](../../../includes/win81-md.md)] e no Windows 10.</span><span class="sxs-lookup"><span data-stu-id="90db4-112">This version includes the .NET Framework 2.0 (the release that follows the .NET Framework 1.1), which is supported on [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], and Windows 10.</span></span> <span data-ttu-id="90db4-113">Você sempre deve tentar instalar o aplicativo primeiro para determinar se ele será atualizado automaticamente para uma versão posterior do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="90db4-113">You should always try to install the app first to determine if it will automatically be updated to a later version of the .NET Framework.</span></span> <span data-ttu-id="90db4-114">Caso contrário, entre em contato com seu ISV para obter uma atualização do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="90db4-114">If it does not, contact your ISV for an app update.</span></span>

## <a name="see-also"></a><span data-ttu-id="90db4-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90db4-115">See also</span></span>

<span data-ttu-id="90db4-116">[Migrar do .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)
[Instalar o .NET Framework 3.5 no Windows 10, Windows 8.1 e Windows 8](../../../docs/framework/install/dotnet-35-windows-10.md)</span><span class="sxs-lookup"><span data-stu-id="90db4-116">[Migrating from the .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)
[Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](../../../docs/framework/install/dotnet-35-windows-10.md)</span></span>
