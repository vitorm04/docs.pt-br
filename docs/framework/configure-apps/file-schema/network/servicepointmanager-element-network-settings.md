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
ms.openlocfilehash: b7333016fea2d46285d3c98181c0ca4904c376f8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089122"
---
# <a name="servicepointmanager-element-network-settings"></a><span data-ttu-id="3a805-102">Elemento \<servicePointManager> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="3a805-102">\<servicePointManager> Element (Network Settings)</span></span>
<span data-ttu-id="3a805-103">Configura conexões com recursos de rede.</span><span class="sxs-lookup"><span data-stu-id="3a805-103">Configures connections to network resources.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePointManager>**

## <a name="syntax"></a><span data-ttu-id="3a805-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a805-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a805-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3a805-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3a805-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3a805-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a805-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="3a805-107">Attributes</span></span>  
  
|<span data-ttu-id="3a805-108">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="3a805-108">**Attribute**</span></span>|<span data-ttu-id="3a805-109">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="3a805-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`checkCertificateName`|<span data-ttu-id="3a805-110">Especifica se o sistema deve verificar se o nome no certificado corresponde ao nome de host do servidor antes de usar o certificado.</span><span class="sxs-lookup"><span data-stu-id="3a805-110">Specifies whether the system should verify that the name on the certificate matches the server host name before using the certificate.</span></span> <span data-ttu-id="3a805-111">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="3a805-111">The default value is `true`.</span></span>|  
|`checkCertificateRevocationList`|<span data-ttu-id="3a805-112">Especifica se o sistema deve verificar se o certificado foi revogado antes de usar o certificado.</span><span class="sxs-lookup"><span data-stu-id="3a805-112">Specifies whether the system should check whether the certificate has been revoked before using the certificate.</span></span> <span data-ttu-id="3a805-113">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="3a805-113">The default value is `false`.</span></span>|  
|`dnsRefreshTimeout`|<span data-ttu-id="3a805-114">Especifica por quanto tempo as resoluções de DNS (serviço de nomes de domínio) são armazenadas em cache em conjunto com a opção Round Robin do DNS, em milissegundos.</span><span class="sxs-lookup"><span data-stu-id="3a805-114">Specifies how long Domain Name Service (DNS) resolutions are cached in conjunction with the DNS Round Robin option, in milliseconds.</span></span> <span data-ttu-id="3a805-115">O valor padrão é de 120.000 milissegundos (dois minutos).</span><span class="sxs-lookup"><span data-stu-id="3a805-115">The default value is 120,000 milliseconds (two minutes).</span></span>|  
|`enableDnsRoundRobin`|<span data-ttu-id="3a805-116">Especifica se as resoluções DNS de nomes de host com vários endereços IP (Internet Protocol) retornam todos os endereços ou apenas o primeiro.</span><span class="sxs-lookup"><span data-stu-id="3a805-116">Specifies whether DNS resolutions of host names with multiple Internet Protocol (IP) addresses return all the addresses, or just the first one.</span></span> <span data-ttu-id="3a805-117">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="3a805-117">The default value is `false`.</span></span>|  
|`encryptionPolicy`|<span data-ttu-id="3a805-118">Especifica a política de criptografia aplicada a uma sessão SSL/TLS em uma <xref:System.Net.ServicePointManager> instância.</span><span class="sxs-lookup"><span data-stu-id="3a805-118">Specifies the encryption policy applied to an SSL/TLS session on a <xref:System.Net.ServicePointManager> instance.</span></span> <span data-ttu-id="3a805-119">Os valores possíveis são equivalentes aos valores da <xref:System.Net.Security.EncryptionPolicy> enumeração.</span><span class="sxs-lookup"><span data-stu-id="3a805-119">The possible values are equivalent to the values for the <xref:System.Net.Security.EncryptionPolicy> enumeration.</span></span> <span data-ttu-id="3a805-120">O uso de <xref:System.Security.Authentication.CipherAlgorithmType.Null> é necessário quando a política de criptografia é definida como `NoEncryption` .</span><span class="sxs-lookup"><span data-stu-id="3a805-120">The use of <xref:System.Security.Authentication.CipherAlgorithmType.Null> is required when the encryption policy is set to `NoEncryption`.</span></span> <span data-ttu-id="3a805-121">O valor padrão é `RequireEncryption`.</span><span class="sxs-lookup"><span data-stu-id="3a805-121">The default value is `RequireEncryption`.</span></span>|  
|`expect100Continue`|<span data-ttu-id="3a805-122">Especifica se os métodos POST devem esperar receber uma `100-continue` resposta do servidor.</span><span class="sxs-lookup"><span data-stu-id="3a805-122">Specifies whether POST methods should expect to receive a `100-continue` response from the server.</span></span> <span data-ttu-id="3a805-123">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="3a805-123">The default value is `true`.</span></span>|  
|`useNagleAlgorithm`|<span data-ttu-id="3a805-124">Especifica se as conexões controladas pelo Gerenciador de ponto de serviço usam o algoritmo Nagle.</span><span class="sxs-lookup"><span data-stu-id="3a805-124">Specifies whether connections controlled by the service point manager use the Nagle algorithm.</span></span> <span data-ttu-id="3a805-125">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="3a805-125">The default value is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a805-126">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3a805-126">Child Elements</span></span>  
 <span data-ttu-id="3a805-127">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="3a805-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3a805-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3a805-128">Parent Elements</span></span>  
  
|<span data-ttu-id="3a805-129">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="3a805-129">**Element**</span></span>|<span data-ttu-id="3a805-130">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="3a805-130">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3a805-131">Configurações</span><span class="sxs-lookup"><span data-stu-id="3a805-131">Settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="3a805-132">Configura as opções de rede básicaspara o namespace <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="3a805-132">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a805-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="3a805-133">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="3a805-134">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="3a805-134">Configuration Files</span></span>  
 <span data-ttu-id="3a805-135">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="3a805-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a805-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="3a805-136">See also</span></span>

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [<span data-ttu-id="3a805-137">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="3a805-137">Network Settings Schema</span></span>](index.md)
