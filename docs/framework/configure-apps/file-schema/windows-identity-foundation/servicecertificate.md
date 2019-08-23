---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: a3aba5618855f7225dc8a427516eaa72b45f6e8b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942407"
---
# <a name="servicecertificate"></a><span data-ttu-id="a55e0-101">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="a55e0-101">\<serviceCertificate></span></span>
<span data-ttu-id="a55e0-102">Configura o certificado X. 509 que é usado para criptografar e descriptografar tokens.</span><span class="sxs-lookup"><span data-stu-id="a55e0-102">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="a55e0-103">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="a55e0-103">\<system.identityModel.services></span></span>  
<span data-ttu-id="a55e0-104">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="a55e0-104">\<federationConfiguration></span></span>  
<span data-ttu-id="a55e0-105">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="a55e0-105">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a55e0-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a55e0-106">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a55e0-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a55e0-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a55e0-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a55e0-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a55e0-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="a55e0-109">Attributes</span></span>  
 <span data-ttu-id="a55e0-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a55e0-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a55e0-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a55e0-111">Child Elements</span></span>  
  
|<span data-ttu-id="a55e0-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="a55e0-112">Element</span></span>|<span data-ttu-id="a55e0-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="a55e0-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a55e0-114">\<certificateReference></span><span class="sxs-lookup"><span data-stu-id="a55e0-114">\<certificateReference></span></span>](certificatereference.md)|<span data-ttu-id="a55e0-115">Especifica as configurações que são usadas para localizar e validar um certificado X. 509 em um repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="a55e0-115">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a55e0-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a55e0-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a55e0-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="a55e0-117">Element</span></span>|<span data-ttu-id="a55e0-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="a55e0-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a55e0-119">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="a55e0-119">\<federationConfiguration></span></span>](federationconfiguration.md)|<span data-ttu-id="a55e0-120">Contém as configurações que definem <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> o (WSFAM) e <xref:System.IdentityModel.Services.SessionAuthenticationModule> o (Sam).</span><span class="sxs-lookup"><span data-stu-id="a55e0-120">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a55e0-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a55e0-121">Example</span></span>  
 <span data-ttu-id="a55e0-122">O XML a seguir mostra o uso do \<elemento > do próprio certificado.</span><span class="sxs-lookup"><span data-stu-id="a55e0-122">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="a55e0-123">O XML é extraído do `CustomToken` exemplo.</span><span class="sxs-lookup"><span data-stu-id="a55e0-123">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
