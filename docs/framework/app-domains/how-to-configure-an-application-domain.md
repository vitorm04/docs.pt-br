---
title: "Como configurar um domínio de aplicativo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, configuring
- ApplicationBase property
ms.assetid: 07ea8438-7a34-49f0-a7e8-3d6ff7e4a482
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 890a8b31339715a4dac8fd2c6e76cc11cda0ee4e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-an-application-domain"></a><span data-ttu-id="d3b45-102">Como configurar um domínio de aplicativo</span><span class="sxs-lookup"><span data-stu-id="d3b45-102">How to: Configure an Application Domain</span></span>
<span data-ttu-id="d3b45-103">Você pode fornecer o Common Language Runtime com informações de configuração para um novo domínio de aplicativo usando a classe <xref:System.AppDomainSetup>.</span><span class="sxs-lookup"><span data-stu-id="d3b45-103">You can provide the common language runtime with configuration information for a new application domain using the <xref:System.AppDomainSetup> class.</span></span> <span data-ttu-id="d3b45-104">Ao criar seus próprios domínios de aplicativo, a propriedade mais importante é <xref:System.AppDomainSetup.ApplicationBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="d3b45-104">When creating your own application domains, the most important property is <xref:System.AppDomainSetup.ApplicationBase%2A>.</span></span> <span data-ttu-id="d3b45-105">As outras propriedades **AppDomainSetup** são usadas principalmente por hosts de tempo de execução para configurar um domínio de aplicativo específico.</span><span class="sxs-lookup"><span data-stu-id="d3b45-105">The other **AppDomainSetup** properties are used mainly by runtime hosts to configure a particular application domain.</span></span>  
  
 <span data-ttu-id="d3b45-106">A propriedade **ApplicationBase** define o diretório raiz do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d3b45-106">The **ApplicationBase** property defines the root directory of the application.</span></span> <span data-ttu-id="d3b45-107">Quando o tempo de execução precisar atender a uma solicitação de tipo, ele investigará em busca do assembly que contém o tipo no diretório especificado pela propriedade **ApplicationBase**.</span><span class="sxs-lookup"><span data-stu-id="d3b45-107">When the runtime needs to satisfy a type request, it probes for the assembly containing the type in the directory specified by the **ApplicationBase** property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3b45-108">Um novo domínio de aplicativo herdará apenas a propriedade **ApplicationBase** do criador.</span><span class="sxs-lookup"><span data-stu-id="d3b45-108">A new application domain inherits only the **ApplicationBase** property of the creator.</span></span>  
  
 <span data-ttu-id="d3b45-109">O exemplo a seguir cria uma instância da classe **AppDomainSetup**, usa essa classe para criar um novo domínio de aplicativo, escreve as informações no console e então descarrega o domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d3b45-109">The following example creates an instance of the **AppDomainSetup** class, uses this class to create a new application domain, writes the information to console, and then unloads the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3b45-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d3b45-110">Example</span></span>  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d3b45-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d3b45-111">See Also</span></span>  
 [<span data-ttu-id="d3b45-112">Programação com domínios do aplicativo</span><span class="sxs-lookup"><span data-stu-id="d3b45-112">Programming with Application Domains</span></span>](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [<span data-ttu-id="d3b45-113">Usar domínios do aplicativo</span><span class="sxs-lookup"><span data-stu-id="d3b45-113">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
