---
title: '&lt;serviceCertificate&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 1373d1e95a0e569f5e5cf433d305d008b4daf838
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicecertificategt"></a><span data-ttu-id="0fc72-102">&lt;serviceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="0fc72-102">&lt;serviceCertificate&gt;</span></span>
<span data-ttu-id="0fc72-103">Configura o certificado x. 509 que é usado para criptografar e descriptografar tokens.</span><span class="sxs-lookup"><span data-stu-id="0fc72-103">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="0fc72-104">\<System ></span><span class="sxs-lookup"><span data-stu-id="0fc72-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="0fc72-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="0fc72-105">\<federationConfiguration></span></span>  
<span data-ttu-id="0fc72-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="0fc72-106">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fc72-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0fc72-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fc72-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0fc72-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0fc72-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0fc72-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fc72-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="0fc72-110">Attributes</span></span>  
 <span data-ttu-id="0fc72-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="0fc72-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0fc72-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0fc72-112">Child Elements</span></span>  
  
|<span data-ttu-id="0fc72-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="0fc72-113">Element</span></span>|<span data-ttu-id="0fc72-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="0fc72-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0fc72-115">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="0fc72-115">\<certificateReference></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|<span data-ttu-id="0fc72-116">Especifica configurações que são usadas para encontrar e validar um certificado x. 509 em um repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="0fc72-116">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0fc72-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0fc72-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0fc72-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="0fc72-118">Element</span></span>|<span data-ttu-id="0fc72-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="0fc72-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0fc72-120">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="0fc72-120">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="0fc72-121">Contém as configurações que definir o <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) e o <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span><span class="sxs-lookup"><span data-stu-id="0fc72-121">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0fc72-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0fc72-122">Example</span></span>  
 <span data-ttu-id="0fc72-123">O XML a seguir mostra o uso do \<serviceCertificate > elemento.</span><span class="sxs-lookup"><span data-stu-id="0fc72-123">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="0fc72-124">O XML é obtido o `CustomToken` exemplo.</span><span class="sxs-lookup"><span data-stu-id="0fc72-124">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
