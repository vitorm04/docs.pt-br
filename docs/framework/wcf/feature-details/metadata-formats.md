---
title: Formatos de metadados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d250b57282d24780dcdd1e045f18d7528bd86a90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="metadata-formats"></a><span data-ttu-id="f953b-102">Formatos de metadados</span><span class="sxs-lookup"><span data-stu-id="f953b-102">Metadata Formats</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="f953b-103">oferece suporte os formatos de metadados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="f953b-103"> supports the metadata formats in the following table.</span></span>  
  
## <a name="metadata-specifications-and-usage"></a><span data-ttu-id="f953b-104">Especificações de metadados e de uso</span><span class="sxs-lookup"><span data-stu-id="f953b-104">Metadata Specifications and Usage</span></span>  
  
|<span data-ttu-id="f953b-105">Protocolo</span><span class="sxs-lookup"><span data-stu-id="f953b-105">Protocol</span></span>|<span data-ttu-id="f953b-106">Especificação e uso</span><span class="sxs-lookup"><span data-stu-id="f953b-106">Specification and usage</span></span>|  
|--------------|-----------------------------|  
|<span data-ttu-id="f953b-107">WSDL 1.1</span><span class="sxs-lookup"><span data-stu-id="f953b-107">WSDL 1.1</span></span>|[<span data-ttu-id="f953b-108">Web Services Description Language (WSDL) 1.1</span><span class="sxs-lookup"><span data-stu-id="f953b-108">Web Services Description Language (WSDL) 1.1</span></span>](http://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f953b-109">usa o WSDL Web Services Description Language () para descrever serviços.</span><span class="sxs-lookup"><span data-stu-id="f953b-109"> uses Web Services Description Language (WSDL) to describe services.</span></span>|  
|<span data-ttu-id="f953b-110">esquema XML</span><span class="sxs-lookup"><span data-stu-id="f953b-110">XML Schema</span></span>|<span data-ttu-id="f953b-111">[Esquema XML parte 2: Edição de segundo de tipos de dados](http://go.microsoft.com/fwlink/?LinkId=94861) e [esquema XML parte 1: estruturas segunda edição](http://go.microsoft.com/fwlink/?LinkId=94862)</span><span class="sxs-lookup"><span data-stu-id="f953b-111">[XML Schema Part 2: Datatypes Second Edition](http://go.microsoft.com/fwlink/?LinkId=94861) and [XML Schema Part 1: Structures Second Edition](http://go.microsoft.com/fwlink/?LinkId=94862)</span></span><br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f953b-112">usa o esquema XML para descrever tipos de dados usados em mensagens.</span><span class="sxs-lookup"><span data-stu-id="f953b-112"> uses the XML Schema to describe data types used in messages.</span></span>|  
|<span data-ttu-id="f953b-113">Política de WS</span><span class="sxs-lookup"><span data-stu-id="f953b-113">WS Policy</span></span>|[<span data-ttu-id="f953b-114">Política de serviços Web 1.2 - Framework (WS-Policy)</span><span class="sxs-lookup"><span data-stu-id="f953b-114">Web Services Policy 1.2 - Framework (WS-Policy)</span></span>](http://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [<span data-ttu-id="f953b-115">Política de serviços Web 1.5 - estrutura</span><span class="sxs-lookup"><span data-stu-id="f953b-115">Web Services Policy 1.5 - Framework</span></span>](http://go.microsoft.com/fwlink/?LinkId=94865)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f953b-116">usa o WS-Policy 1.2 ou 1,5 especificações com declarações específicas de domínio para descrever os recursos e requisitos de serviço.</span><span class="sxs-lookup"><span data-stu-id="f953b-116"> uses the WS-Policy 1.2 or 1.5 specifications with domain-specific assertions to describe service requirements and capabilities.</span></span>|  
|<span data-ttu-id="f953b-117">Anexos de política WS</span><span class="sxs-lookup"><span data-stu-id="f953b-117">WS Policy Attachments</span></span>|[<span data-ttu-id="f953b-118">Política de serviços Web 1.2 - anexo (mecanismo WS-PolicyAttachment)</span><span class="sxs-lookup"><span data-stu-id="f953b-118">Web Services Policy 1.2 - Attachment (WS-PolicyAttachment)</span></span>](http://go.microsoft.com/fwlink/?LinkId=94866)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f953b-119">implementa o WS-Policy anexos para anexar a expressões de política em vários escopos em WSDL.</span><span class="sxs-lookup"><span data-stu-id="f953b-119"> implements WS-Policy Attachments to attach policy expressions at various scopes in WSDL.</span></span>|  
|<span data-ttu-id="f953b-120">Troca de metadados de WS</span><span class="sxs-lookup"><span data-stu-id="f953b-120">WS Metadata Exchange</span></span>|[<span data-ttu-id="f953b-121">Troca de metadados de serviços da Web (WS-MetadataExchange) versão 1.1</span><span class="sxs-lookup"><span data-stu-id="f953b-121">Web Services Metadata Exchange (WS-MetadataExchange) version 1.1</span></span>](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f953b-122">implementa o WS-MetadataExchange para recuperar o esquema XML, WSDL e WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="f953b-122"> implements WS-MetadataExchange to retrieve XML Schema, WSDL, and WS-Policy.</span></span>|  
|<span data-ttu-id="f953b-123">WS endereçamento de associação para WSDL</span><span class="sxs-lookup"><span data-stu-id="f953b-123">WS Addressing Binding for WSDL</span></span>|[<span data-ttu-id="f953b-124">Associação de WSDL 1.0 - endereçamento de serviços Web</span><span class="sxs-lookup"><span data-stu-id="f953b-124">Web Services Addressing 1.0 - WSDL Binding</span></span>](http://go.microsoft.com/fwlink/?LinkId=94869)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f953b-125">implementa o WS-Addressing associação WSDL anexar informações de endereçamento em WSDL.</span><span class="sxs-lookup"><span data-stu-id="f953b-125"> implements WS-Addressing Binding for WSDL to attach addressing information in WSDL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f953b-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f953b-126">See Also</span></span>  
 [<span data-ttu-id="f953b-127">Protocolos com suporte por associações de interoperabilidade fornecidas pelo sistema de serviços Web</span><span class="sxs-lookup"><span data-stu-id="f953b-127">Web Services Protocols Supported by System-Provided Interoperability Bindings</span></span>](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
 [<span data-ttu-id="f953b-128">WSDL e política</span><span class="sxs-lookup"><span data-stu-id="f953b-128">WSDL and Policy</span></span>](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)
