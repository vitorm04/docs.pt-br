---
title: Elemento <servicePointManager> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
ms.openlocfilehash: 95ad1880cbb832a17311e7e63e9203f53257f65f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697709"
---
# <a name="servicepointmanager-element-network-settings"></a><span data-ttu-id="40079-102">\<servicePointManager > elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="40079-102">\<servicePointManager> Element (Network Settings)</span></span>
<span data-ttu-id="40079-103">Configura conexões com recursos de rede.</span><span class="sxs-lookup"><span data-stu-id="40079-103">Configures connections to network resources.</span></span>  
  
[<span data-ttu-id="40079-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="40079-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="40079-105">&nbsp; @ no__t-1[ **@no__t -4System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="40079-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="40079-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<settings >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="40079-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>  
<span data-ttu-id="40079-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<servicePointManager >**</span><span class="sxs-lookup"><span data-stu-id="40079-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePointManager>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40079-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="40079-108">Syntax</span></span>  
  
```xml  
<servicePointManager  
  checkCertificateName="true|false"  
  checkCertificateRevocationList="true|false"  
  encryptionPolicy="AllowNoEncryption|NoEncryption|RequireEncryption"  
  expect100Continue="true|false"  
  useNagleAlgorithm="true|false"  
  enableDnsRoundRobin="true|false"  
  dnsRefreshTimeout="time"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40079-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="40079-109">Attributes and Elements</span></span>  
 <span data-ttu-id="40079-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="40079-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40079-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="40079-111">Attributes</span></span>  
  
|<span data-ttu-id="40079-112">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="40079-112">**Attribute**</span></span>|<span data-ttu-id="40079-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="40079-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`checkCertificateName`|<span data-ttu-id="40079-114">Especifica se o sistema deve verificar se o nome no certificado corresponde ao nome de host do servidor antes de usar o certificado.</span><span class="sxs-lookup"><span data-stu-id="40079-114">Specifies whether the system should verify that the name on the certificate matches the server host name before using the certificate.</span></span> <span data-ttu-id="40079-115">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="40079-115">The default value is `true`.</span></span>|  
|`checkCertificateRevocationList`|<span data-ttu-id="40079-116">Especifica se o sistema deve verificar se o certificado foi revogado antes de usar o certificado.</span><span class="sxs-lookup"><span data-stu-id="40079-116">Specifies whether the system should check whether the certificate has been revoked before using the certificate.</span></span> <span data-ttu-id="40079-117">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="40079-117">The default value is `false`.</span></span>|  
|`dnsRefreshTimeout`|<span data-ttu-id="40079-118">Especifica por quanto tempo as resoluções de DNS (serviço de nomes de domínio) são armazenadas em cache em conjunto com a opção Round Robin do DNS, em milissegundos.</span><span class="sxs-lookup"><span data-stu-id="40079-118">Specifies how long Domain Name Service (DNS) resolutions are cached in conjunction with the DNS Round Robin option, in milliseconds.</span></span> <span data-ttu-id="40079-119">O valor padrão é de 120.000 milissegundos (dois minutos).</span><span class="sxs-lookup"><span data-stu-id="40079-119">The default value is 120,000 milliseconds (two minutes).</span></span>|  
|`enableDnsRoundRobin`|<span data-ttu-id="40079-120">Especifica se as resoluções DNS de nomes de host com vários endereços IP (Internet Protocol) retornam todos os endereços ou apenas o primeiro.</span><span class="sxs-lookup"><span data-stu-id="40079-120">Specifies whether DNS resolutions of host names with multiple Internet Protocol (IP) addresses return all the addresses, or just the first one.</span></span> <span data-ttu-id="40079-121">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="40079-121">The default value is `false`.</span></span>|  
|`encryptionPolicy`|<span data-ttu-id="40079-122">Especifica a política de criptografia aplicada a uma sessão SSL/TLS em uma instância <xref:System.Net.ServicePointManager>.</span><span class="sxs-lookup"><span data-stu-id="40079-122">Specifies the encryption policy applied to an SSL/TLS session on a <xref:System.Net.ServicePointManager> instance.</span></span> <span data-ttu-id="40079-123">Os valores possíveis são equivalentes aos valores para a enumeração <xref:System.Net.Security.EncryptionPolicy>.</span><span class="sxs-lookup"><span data-stu-id="40079-123">The possible values are equivalent to the values for the <xref:System.Net.Security.EncryptionPolicy> enumeration.</span></span> <span data-ttu-id="40079-124">O uso de <xref:System.Security.Authentication.CipherAlgorithmType.Null> é necessário quando a política de criptografia é definida como `NoEncryption`.</span><span class="sxs-lookup"><span data-stu-id="40079-124">The use of <xref:System.Security.Authentication.CipherAlgorithmType.Null> is required when the encryption policy is set to `NoEncryption`.</span></span> <span data-ttu-id="40079-125">O valor padrão é `RequireEncryption`.</span><span class="sxs-lookup"><span data-stu-id="40079-125">The default value is `RequireEncryption`.</span></span>|  
|`expect100Continue`|<span data-ttu-id="40079-126">Especifica se os métodos POST devem esperar receber uma resposta `100-continue` do servidor.</span><span class="sxs-lookup"><span data-stu-id="40079-126">Specifies whether POST methods should expect to receive a `100-continue` response from the server.</span></span> <span data-ttu-id="40079-127">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="40079-127">The default value is `true`.</span></span>|  
|`useNagleAlgorithm`|<span data-ttu-id="40079-128">Especifica se as conexões controladas pelo Gerenciador de ponto de serviço usam o algoritmo Nagle.</span><span class="sxs-lookup"><span data-stu-id="40079-128">Specifies whether connections controlled by the service point manager use the Nagle algorithm.</span></span> <span data-ttu-id="40079-129">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="40079-129">The default value is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="40079-130">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="40079-130">Child Elements</span></span>  
 <span data-ttu-id="40079-131">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="40079-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="40079-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="40079-132">Parent Elements</span></span>  
  
|<span data-ttu-id="40079-133">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="40079-133">**Element**</span></span>|<span data-ttu-id="40079-134">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="40079-134">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="40079-135">Configurações</span><span class="sxs-lookup"><span data-stu-id="40079-135">Settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="40079-136">Configura as opções de rede básicaspara o namespace <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="40079-136">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40079-137">Comentários</span><span class="sxs-lookup"><span data-stu-id="40079-137">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="40079-138">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="40079-138">Configuration Files</span></span>  
 <span data-ttu-id="40079-139">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="40079-139">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40079-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40079-140">See also</span></span>

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [<span data-ttu-id="40079-141">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="40079-141">Network Settings Schema</span></span>](index.md)
