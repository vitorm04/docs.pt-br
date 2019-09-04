---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: 653dd9cfadbfd33f5371b77172199b946321bc8c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251864"
---
# <a name="servicecertificate"></a><span data-ttu-id="0c655-101">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="0c655-101">\<serviceCertificate></span></span>
<span data-ttu-id="0c655-102">Configura o certificado X. 509 que é usado para criptografar e descriptografar tokens.</span><span class="sxs-lookup"><span data-stu-id="0c655-102">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
<span data-ttu-id="0c655-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0c655-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0c655-104">&nbsp;&nbsp;[ **\<System. identityModel. Services >** ](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="0c655-104">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="0c655-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> federationConfiguration**](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="0c655-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="0c655-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de certificados**</span><span class="sxs-lookup"><span data-stu-id="0c655-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c655-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0c655-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c655-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0c655-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0c655-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0c655-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c655-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="0c655-110">Attributes</span></span>  
 <span data-ttu-id="0c655-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="0c655-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0c655-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0c655-112">Child Elements</span></span>  
  
|<span data-ttu-id="0c655-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="0c655-113">Element</span></span>|<span data-ttu-id="0c655-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c655-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c655-115">\<certificateReference></span><span class="sxs-lookup"><span data-stu-id="0c655-115">\<certificateReference></span></span>](certificatereference.md)|<span data-ttu-id="0c655-116">Especifica as configurações que são usadas para localizar e validar um certificado X. 509 em um repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="0c655-116">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0c655-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0c655-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0c655-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="0c655-118">Element</span></span>|<span data-ttu-id="0c655-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c655-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c655-120">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="0c655-120">\<federationConfiguration></span></span>](federationconfiguration.md)|<span data-ttu-id="0c655-121">Contém as configurações que definem <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> o (WSFAM) e <xref:System.IdentityModel.Services.SessionAuthenticationModule> o (Sam).</span><span class="sxs-lookup"><span data-stu-id="0c655-121">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0c655-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0c655-122">Example</span></span>  
 <span data-ttu-id="0c655-123">O XML a seguir mostra o uso do \<elemento > do próprio certificado.</span><span class="sxs-lookup"><span data-stu-id="0c655-123">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="0c655-124">O XML é extraído do `CustomToken` exemplo.</span><span class="sxs-lookup"><span data-stu-id="0c655-124">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
