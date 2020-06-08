---
title: Elemento <servicePointManager> (Configurações de Rede)
description: O <servicePointManager> elemento de configurações de rede configura conexões com opções de recursos de rede no .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
ms.openlocfilehash: eb27716ec7c2936f32a7e4d4c983d1e175c4d044
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504518"
---
# <a name="servicepointmanager-element-network-settings"></a><span data-ttu-id="b49d5-103">Elemento \<servicePointManager> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="b49d5-103">\<servicePointManager> Element (Network Settings)</span></span>
<span data-ttu-id="b49d5-104">Configura conexões com recursos de rede.</span><span class="sxs-lookup"><span data-stu-id="b49d5-104">Configures connections to network resources.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePointManager>**

## <a name="syntax"></a><span data-ttu-id="b49d5-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b49d5-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b49d5-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b49d5-106">Attributes and Elements</span></span>  
 <span data-ttu-id="b49d5-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b49d5-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b49d5-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="b49d5-108">Attributes</span></span>  
  
|<span data-ttu-id="b49d5-109">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="b49d5-109">**Attribute**</span></span>|<span data-ttu-id="b49d5-110">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="b49d5-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`checkCertificateName`|<span data-ttu-id="b49d5-111">Especifica se o sistema deve verificar se o nome no certificado corresponde ao nome de host do servidor antes de usar o certificado.</span><span class="sxs-lookup"><span data-stu-id="b49d5-111">Specifies whether the system should verify that the name on the certificate matches the server host name before using the certificate.</span></span> <span data-ttu-id="b49d5-112">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="b49d5-112">The default value is `true`.</span></span>|  
|`checkCertificateRevocationList`|<span data-ttu-id="b49d5-113">Especifica se o sistema deve verificar se o certificado foi revogado antes de usar o certificado.</span><span class="sxs-lookup"><span data-stu-id="b49d5-113">Specifies whether the system should check whether the certificate has been revoked before using the certificate.</span></span> <span data-ttu-id="b49d5-114">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="b49d5-114">The default value is `false`.</span></span>|  
|`dnsRefreshTimeout`|<span data-ttu-id="b49d5-115">Especifica por quanto tempo as resoluções de DNS (serviço de nomes de domínio) são armazenadas em cache em conjunto com a opção Round Robin do DNS, em milissegundos.</span><span class="sxs-lookup"><span data-stu-id="b49d5-115">Specifies how long Domain Name Service (DNS) resolutions are cached in conjunction with the DNS Round Robin option, in milliseconds.</span></span> <span data-ttu-id="b49d5-116">O valor padrão é de 120.000 milissegundos (dois minutos).</span><span class="sxs-lookup"><span data-stu-id="b49d5-116">The default value is 120,000 milliseconds (two minutes).</span></span>|  
|`enableDnsRoundRobin`|<span data-ttu-id="b49d5-117">Especifica se as resoluções DNS de nomes de host com vários endereços IP (Internet Protocol) retornam todos os endereços ou apenas o primeiro.</span><span class="sxs-lookup"><span data-stu-id="b49d5-117">Specifies whether DNS resolutions of host names with multiple Internet Protocol (IP) addresses return all the addresses, or just the first one.</span></span> <span data-ttu-id="b49d5-118">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="b49d5-118">The default value is `false`.</span></span>|  
|`encryptionPolicy`|<span data-ttu-id="b49d5-119">Especifica a política de criptografia aplicada a uma sessão SSL/TLS em uma <xref:System.Net.ServicePointManager> instância.</span><span class="sxs-lookup"><span data-stu-id="b49d5-119">Specifies the encryption policy applied to an SSL/TLS session on a <xref:System.Net.ServicePointManager> instance.</span></span> <span data-ttu-id="b49d5-120">Os valores possíveis são equivalentes aos valores da <xref:System.Net.Security.EncryptionPolicy> enumeração.</span><span class="sxs-lookup"><span data-stu-id="b49d5-120">The possible values are equivalent to the values for the <xref:System.Net.Security.EncryptionPolicy> enumeration.</span></span> <span data-ttu-id="b49d5-121">O uso de <xref:System.Security.Authentication.CipherAlgorithmType.Null> é necessário quando a política de criptografia é definida como `NoEncryption` .</span><span class="sxs-lookup"><span data-stu-id="b49d5-121">The use of <xref:System.Security.Authentication.CipherAlgorithmType.Null> is required when the encryption policy is set to `NoEncryption`.</span></span> <span data-ttu-id="b49d5-122">O valor padrão é `RequireEncryption`.</span><span class="sxs-lookup"><span data-stu-id="b49d5-122">The default value is `RequireEncryption`.</span></span>|  
|`expect100Continue`|<span data-ttu-id="b49d5-123">Especifica se os métodos POST devem esperar receber uma `100-continue` resposta do servidor.</span><span class="sxs-lookup"><span data-stu-id="b49d5-123">Specifies whether POST methods should expect to receive a `100-continue` response from the server.</span></span> <span data-ttu-id="b49d5-124">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="b49d5-124">The default value is `true`.</span></span>|  
|`useNagleAlgorithm`|<span data-ttu-id="b49d5-125">Especifica se as conexões controladas pelo Gerenciador de ponto de serviço usam o algoritmo Nagle.</span><span class="sxs-lookup"><span data-stu-id="b49d5-125">Specifies whether connections controlled by the service point manager use the Nagle algorithm.</span></span> <span data-ttu-id="b49d5-126">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="b49d5-126">The default value is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b49d5-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b49d5-127">Child Elements</span></span>  
 <span data-ttu-id="b49d5-128">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b49d5-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b49d5-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b49d5-129">Parent Elements</span></span>  
  
|<span data-ttu-id="b49d5-130">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="b49d5-130">**Element**</span></span>|<span data-ttu-id="b49d5-131">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="b49d5-131">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b49d5-132">Configurações</span><span class="sxs-lookup"><span data-stu-id="b49d5-132">Settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="b49d5-133">Configura as opções de rede básicaspara o namespace <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="b49d5-133">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b49d5-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="b49d5-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b49d5-135">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="b49d5-135">Configuration Files</span></span>  
 <span data-ttu-id="b49d5-136">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="b49d5-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b49d5-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="b49d5-137">See also</span></span>

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [<span data-ttu-id="b49d5-138">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="b49d5-138">Network Settings Schema</span></span>](index.md)
