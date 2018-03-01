---
title: Estendendo o sistema de metadados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- extending metadata [WCF]
ms.assetid: 8c6b3b00-61b8-4589-8fa5-546cc33719bf
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: aca7a7aba7ef4a40100e9858561d197916b71544
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="extending-the-metadata-system"></a><span data-ttu-id="a3fc6-102">Estendendo o sistema de metadados</span><span class="sxs-lookup"><span data-stu-id="a3fc6-102">Extending the Metadata System</span></span>
<span data-ttu-id="a3fc6-103">O [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sistema de metadados é um grupo de interfaces e classes que representam os metadados necessários para implementar aplicativos baseados em serviço.</span><span class="sxs-lookup"><span data-stu-id="a3fc6-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] metadata system is a group of classes and interfaces that represent metadata required to implement service-based applications.</span></span> <span data-ttu-id="a3fc6-104">Modificar ou estender as classes de ou implementar e configurar as interfaces para exportar e importar metadados personalizados, como extensões WSDL Web Services Description Language () ou asserções de WS-PolicyAttachments personalizadas.</span><span class="sxs-lookup"><span data-stu-id="a3fc6-104">Modify or extend the classes or implement and configure the interfaces to export and import custom metadata such as Web Services Description Language (WSDL) extensions or custom WS-PolicyAttachments assertions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a3fc6-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="a3fc6-105">In This Section</span></span>  
 [<span data-ttu-id="a3fc6-106">Exportando metadados personalizados para uma extensão do WCF</span><span class="sxs-lookup"><span data-stu-id="a3fc6-106">Exporting Custom Metadata for a WCF Extension</span></span>](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)  
 <span data-ttu-id="a3fc6-107">Descreve como implementar e usar o <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface incorporar declarações de política personalizada em documentos WSDL.</span><span class="sxs-lookup"><span data-stu-id="a3fc6-107">Describes how to implement and use the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface to embed custom policy assertions in WSDL documents.</span></span>  
  
 [<span data-ttu-id="a3fc6-108">Importando metadados personalizados para uma extensão do WCF</span><span class="sxs-lookup"><span data-stu-id="a3fc6-108">Importing Custom Metadata for a WCF Extension</span></span>](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)  
 <span data-ttu-id="a3fc6-109">Descreve como implementar e usar o <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interface para ler e responder às declarações de política personalizada em documentos WSDL.</span><span class="sxs-lookup"><span data-stu-id="a3fc6-109">Describes how to implement and use the <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interface to read and respond to custom policy assertions in WSDL documents.</span></span>  
  
 [<span data-ttu-id="a3fc6-110">Publicando e recuperando metadados através de uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="a3fc6-110">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 <span data-ttu-id="a3fc6-111">Descreve como a troca de metadados sobre associações personalizadas.</span><span class="sxs-lookup"><span data-stu-id="a3fc6-111">Describes how to exchange metadata over custom bindings.</span></span>
