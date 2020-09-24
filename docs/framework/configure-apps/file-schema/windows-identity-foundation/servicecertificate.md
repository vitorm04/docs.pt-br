---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: ce8be6eea5469b099a368a0b62e791faa7e3cbfc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156986"
---
# \<serviceCertificate>

<span data-ttu-id="15cf3-101">Configura o certificado X. 509 que é usado para criptografar e descriptografar tokens.</span><span class="sxs-lookup"><span data-stu-id="15cf3-101">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="15cf3-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="15cf3-102">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15cf3-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="15cf3-103">Attributes and Elements</span></span>  

 <span data-ttu-id="15cf3-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="15cf3-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15cf3-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="15cf3-105">Attributes</span></span>  

 <span data-ttu-id="15cf3-106">Nenhum</span><span class="sxs-lookup"><span data-stu-id="15cf3-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="15cf3-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="15cf3-107">Child Elements</span></span>  
  
|<span data-ttu-id="15cf3-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="15cf3-108">Element</span></span>|<span data-ttu-id="15cf3-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="15cf3-109">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateReference>](certificatereference.md)|<span data-ttu-id="15cf3-110">Especifica as configurações que são usadas para localizar e validar um certificado X. 509 em um repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="15cf3-110">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="15cf3-111">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="15cf3-111">Parent Elements</span></span>  
  
|<span data-ttu-id="15cf3-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="15cf3-112">Element</span></span>|<span data-ttu-id="15cf3-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="15cf3-113">Description</span></span>|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<span data-ttu-id="15cf3-114">Contém as configurações que definem o <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) e o <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam).</span><span class="sxs-lookup"><span data-stu-id="15cf3-114">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="15cf3-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="15cf3-115">Example</span></span>  

 <span data-ttu-id="15cf3-116">O XML a seguir mostra o uso do \<serviceCertificate> elemento.</span><span class="sxs-lookup"><span data-stu-id="15cf3-116">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="15cf3-117">O XML é extraído do `CustomToken` exemplo.</span><span class="sxs-lookup"><span data-stu-id="15cf3-117">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
