---
title: "Como migrar o código de cliente de serviço Web do ASP.NET para o Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e0a22a7-e1d5-4718-8997-4319a7cd9027
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d77e07cca938b67f5b79416ac4d8fdef96739ed2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-migrate-aspnet-web-service-client-code-to-the-windows-communication-foundation"></a><span data-ttu-id="01f0d-102">Como migrar o código de cliente de serviço Web do ASP.NET para o Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="01f0d-102">How to: Migrate ASP.NET Web Service Client Code to the Windows Communication Foundation</span></span>
<span data-ttu-id="01f0d-103">O procedimento a seguir descreve as etapas gerais que devem ser seguidas para migrar o código de cliente de serviço Web ASP.NET para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="01f0d-103">The following procedure describes the broad steps that need to be followed to migrate ASP.NET Web Service client code to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="01f0d-104">Procedimento</span><span class="sxs-lookup"><span data-stu-id="01f0d-104">Procedure</span></span>  
  
#### <a name="to-migrate-aspnet-web-service-client-code-to-wcf"></a><span data-ttu-id="01f0d-105">Para migrar o código de cliente de serviço Web ASP.NET para o WCF</span><span class="sxs-lookup"><span data-stu-id="01f0d-105">To migrate ASP.NET Web Service client code to WCF</span></span>  
  
1.  <span data-ttu-id="01f0d-106">Certifique-se de que um abrangente conjunto de testes existem para o cliente.</span><span class="sxs-lookup"><span data-stu-id="01f0d-106">Ensure that a comprehensive set of tests exist for the client.</span></span>  
  
2.  <span data-ttu-id="01f0d-107">Use o Visual Studio 2005 para atualizar o aplicativo cliente .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="01f0d-107">Use Visual Studio 2005 to upgrade the client application to .NET 2.0.</span></span> <span data-ttu-id="01f0d-108">Execute o conjunto de testes.</span><span class="sxs-lookup"><span data-stu-id="01f0d-108">Run the set of tests.</span></span>  
  
3.  <span data-ttu-id="01f0d-109">Remova o código de cliente do ASP.NET do projeto cliente.</span><span class="sxs-lookup"><span data-stu-id="01f0d-109">Remove ASP.NET client code from the client project.</span></span> <span data-ttu-id="01f0d-110">Esse código é gerado usando a ferramenta WSDL.exe de módulos.</span><span class="sxs-lookup"><span data-stu-id="01f0d-110">That code is in modules generated using the WSDL.exe tool.</span></span>  
  
4.  <span data-ttu-id="01f0d-111">Gerar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] código de cliente usando o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="01f0d-111">Generate [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client code using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="01f0d-112">Adicione esse código ao projeto de cliente e mesclar a saída de configuração no arquivo de configuração existente do cliente.</span><span class="sxs-lookup"><span data-stu-id="01f0d-112">Add that code to the client project and merge the configuration output into the client’s existing configuration file.</span></span>  
  
5.  <span data-ttu-id="01f0d-113">Compile o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="01f0d-113">Compile the application.</span></span> <span data-ttu-id="01f0d-114">Repare os erros de compilação, substituindo as referências aos tipos de cliente antigos do ASP.NET com referências para o novo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tipos de clientes.</span><span class="sxs-lookup"><span data-stu-id="01f0d-114">Repair the compilation errors by replacing references to the former ASP.NET client types with references to the new [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client types.</span></span>  
  
6.  <span data-ttu-id="01f0d-115">Execute o conjunto de testes.</span><span class="sxs-lookup"><span data-stu-id="01f0d-115">Run the set of tests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01f0d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01f0d-116">See Also</span></span>  
 [<span data-ttu-id="01f0d-117">Como: migrar o código de serviço da Web do ASP.NET para o Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="01f0d-117">How to: Migrate ASP.NET Web Service Code to the Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)
