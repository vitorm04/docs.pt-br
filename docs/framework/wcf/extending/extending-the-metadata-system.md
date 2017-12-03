---
title: Estendendo o sistema de metadados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extending metadata [WCF]
ms.assetid: 8c6b3b00-61b8-4589-8fa5-546cc33719bf
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d0c729850e25e9fe4bec37dc366053de8c56f210
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="extending-the-metadata-system"></a><span data-ttu-id="8e35c-102">Estendendo o sistema de metadados</span><span class="sxs-lookup"><span data-stu-id="8e35c-102">Extending the Metadata System</span></span>
<span data-ttu-id="8e35c-103">O [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sistema de metadados é um grupo de interfaces e classes que representam os metadados necessários para implementar aplicativos baseados em serviço.</span><span class="sxs-lookup"><span data-stu-id="8e35c-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] metadata system is a group of classes and interfaces that represent metadata required to implement service-based applications.</span></span> <span data-ttu-id="8e35c-104">Modificar ou estender as classes de ou implementar e configurar as interfaces para exportar e importar metadados personalizados, como extensões WSDL Web Services Description Language () ou asserções de WS-PolicyAttachments personalizadas.</span><span class="sxs-lookup"><span data-stu-id="8e35c-104">Modify or extend the classes or implement and configure the interfaces to export and import custom metadata such as Web Services Description Language (WSDL) extensions or custom WS-PolicyAttachments assertions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8e35c-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="8e35c-105">In This Section</span></span>  
 [<span data-ttu-id="8e35c-106">Exportando metadados personalizados para uma extensão do WCF</span><span class="sxs-lookup"><span data-stu-id="8e35c-106">Exporting Custom Metadata for a WCF Extension</span></span>](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)  
 <span data-ttu-id="8e35c-107">Descreve como implementar e usar o <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface incorporar declarações de política personalizada em documentos WSDL.</span><span class="sxs-lookup"><span data-stu-id="8e35c-107">Describes how to implement and use the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface to embed custom policy assertions in WSDL documents.</span></span>  
  
 [<span data-ttu-id="8e35c-108">Importando metadados personalizados para uma extensão do WCF</span><span class="sxs-lookup"><span data-stu-id="8e35c-108">Importing Custom Metadata for a WCF Extension</span></span>](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)  
 <span data-ttu-id="8e35c-109">Descreve como implementar e usar o <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interface para ler e responder às declarações de política personalizada em documentos WSDL.</span><span class="sxs-lookup"><span data-stu-id="8e35c-109">Describes how to implement and use the <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interface to read and respond to custom policy assertions in WSDL documents.</span></span>  
  
 [<span data-ttu-id="8e35c-110">Publicando e recuperando metadados através de uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="8e35c-110">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 <span data-ttu-id="8e35c-111">Descreve como a troca de metadados sobre associações personalizadas.</span><span class="sxs-lookup"><span data-stu-id="8e35c-111">Describes how to exchange metadata over custom bindings.</span></span>
