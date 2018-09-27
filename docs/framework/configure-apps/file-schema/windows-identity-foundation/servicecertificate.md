---
title: '&lt;serviceCertificate&gt;'
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: 008d2269a72759117658e27ec130cc8cf62cfdfa
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47400407"
---
# <a name="ltservicecertificategt"></a><span data-ttu-id="02d5b-102">&lt;serviceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="02d5b-102">&lt;serviceCertificate&gt;</span></span>
<span data-ttu-id="02d5b-103">Configura o certificado X.509 que é usado para criptografar e descriptografar tokens.</span><span class="sxs-lookup"><span data-stu-id="02d5b-103">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="02d5b-104">\<IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="02d5b-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="02d5b-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="02d5b-105">\<federationConfiguration></span></span>  
<span data-ttu-id="02d5b-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="02d5b-106">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02d5b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="02d5b-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02d5b-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="02d5b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="02d5b-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="02d5b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02d5b-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="02d5b-110">Attributes</span></span>  
 <span data-ttu-id="02d5b-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="02d5b-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="02d5b-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="02d5b-112">Child Elements</span></span>  
  
|<span data-ttu-id="02d5b-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="02d5b-113">Element</span></span>|<span data-ttu-id="02d5b-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="02d5b-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02d5b-115">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="02d5b-115">\<certificateReference></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|<span data-ttu-id="02d5b-116">Especifica configurações que são usadas para encontrar e validar um certificado x. 509 em um repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="02d5b-116">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="02d5b-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="02d5b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="02d5b-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="02d5b-118">Element</span></span>|<span data-ttu-id="02d5b-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="02d5b-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02d5b-120">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="02d5b-120">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="02d5b-121">Contém as configurações que configuram os <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) e o <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span><span class="sxs-lookup"><span data-stu-id="02d5b-121">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="02d5b-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="02d5b-122">Example</span></span>  
 <span data-ttu-id="02d5b-123">O XML a seguir mostra o uso do \<serviceCertificate > elemento.</span><span class="sxs-lookup"><span data-stu-id="02d5b-123">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="02d5b-124">O XML é obtido a `CustomToken` exemplo.</span><span class="sxs-lookup"><span data-stu-id="02d5b-124">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
