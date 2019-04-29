---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: 328d074f9edc5ddf871308a7e3d694bf94adea78
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793816"
---
# <a name="servicecertificate"></a><span data-ttu-id="d82db-101">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="d82db-101">\<serviceCertificate></span></span>
<span data-ttu-id="d82db-102">Configura o certificado X.509 que é usado para criptografar e descriptografar tokens.</span><span class="sxs-lookup"><span data-stu-id="d82db-102">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="d82db-103">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="d82db-103">\<system.identityModel.services></span></span>  
<span data-ttu-id="d82db-104">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="d82db-104">\<federationConfiguration></span></span>  
<span data-ttu-id="d82db-105">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="d82db-105">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d82db-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d82db-106">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d82db-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d82db-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d82db-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d82db-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d82db-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="d82db-109">Attributes</span></span>  
 <span data-ttu-id="d82db-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d82db-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d82db-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d82db-111">Child Elements</span></span>  
  
|<span data-ttu-id="d82db-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="d82db-112">Element</span></span>|<span data-ttu-id="d82db-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="d82db-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d82db-114">\<certificateReference></span><span class="sxs-lookup"><span data-stu-id="d82db-114">\<certificateReference></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|<span data-ttu-id="d82db-115">Especifica configurações que são usadas para encontrar e validar um certificado x. 509 em um repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="d82db-115">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d82db-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d82db-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d82db-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="d82db-117">Element</span></span>|<span data-ttu-id="d82db-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="d82db-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d82db-119">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="d82db-119">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="d82db-120">Contém as configurações que configuram os <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) e o <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span><span class="sxs-lookup"><span data-stu-id="d82db-120">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d82db-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d82db-121">Example</span></span>  
 <span data-ttu-id="d82db-122">O XML a seguir mostra o uso do \<serviceCertificate > elemento.</span><span class="sxs-lookup"><span data-stu-id="d82db-122">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="d82db-123">O XML é obtido a `CustomToken` exemplo.</span><span class="sxs-lookup"><span data-stu-id="d82db-123">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
