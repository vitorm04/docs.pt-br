---
title: '&lt;serviceCertificate&gt;'
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: 008d2269a72759117658e27ec130cc8cf62cfdfa
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084300"
---
# <a name="ltservicecertificategt"></a><span data-ttu-id="85c4a-102">&lt;serviceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="85c4a-102">&lt;serviceCertificate&gt;</span></span>
<span data-ttu-id="85c4a-103">Configura o certificado X.509 que é usado para criptografar e descriptografar tokens.</span><span class="sxs-lookup"><span data-stu-id="85c4a-103">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="85c4a-104">\<IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="85c4a-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="85c4a-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="85c4a-105">\<federationConfiguration></span></span>  
<span data-ttu-id="85c4a-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="85c4a-106">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85c4a-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="85c4a-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85c4a-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="85c4a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="85c4a-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="85c4a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85c4a-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="85c4a-110">Attributes</span></span>  
 <span data-ttu-id="85c4a-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="85c4a-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="85c4a-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="85c4a-112">Child Elements</span></span>  
  
|<span data-ttu-id="85c4a-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="85c4a-113">Element</span></span>|<span data-ttu-id="85c4a-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="85c4a-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85c4a-115">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="85c4a-115">\<certificateReference></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|<span data-ttu-id="85c4a-116">Especifica configurações que são usadas para encontrar e validar um certificado x. 509 em um repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="85c4a-116">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="85c4a-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="85c4a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="85c4a-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="85c4a-118">Element</span></span>|<span data-ttu-id="85c4a-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="85c4a-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85c4a-120">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="85c4a-120">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="85c4a-121">Contém as configurações que configuram os <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) e o <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span><span class="sxs-lookup"><span data-stu-id="85c4a-121">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="85c4a-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="85c4a-122">Example</span></span>  
 <span data-ttu-id="85c4a-123">O XML a seguir mostra o uso do \<serviceCertificate > elemento.</span><span class="sxs-lookup"><span data-stu-id="85c4a-123">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="85c4a-124">O XML é obtido a `CustomToken` exemplo.</span><span class="sxs-lookup"><span data-stu-id="85c4a-124">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
