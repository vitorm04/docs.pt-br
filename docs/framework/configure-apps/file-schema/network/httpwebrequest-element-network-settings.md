---
title: Elemento <httpWebRequest> (Configurações de Rede)
description: O <httpWebRequest> elemento de configurações de rede personaliza os parâmetros de solicitação da Web no .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
ms.openlocfilehash: 59ab425dcef8ac5283035910a9d78a89a16be8b1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504583"
---
# <a name="httpwebrequest-element-network-settings"></a><span data-ttu-id="c8fb3-103">Elemento \<httpWebRequest> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="c8fb3-103">\<httpWebRequest> Element (Network Settings)</span></span>
<span data-ttu-id="c8fb3-104">Personaliza os parâmetros de solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="c8fb3-104">Customizes Web request parameters.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpWebRequest>**

## <a name="syntax"></a><span data-ttu-id="c8fb3-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c8fb3-105">Syntax</span></span>  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c8fb3-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c8fb3-106">Attributes and Elements</span></span>  
 <span data-ttu-id="c8fb3-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c8fb3-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c8fb3-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="c8fb3-108">Attributes</span></span>  
  
|<span data-ttu-id="c8fb3-109">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="c8fb3-109">**Attribute**</span></span>|<span data-ttu-id="c8fb3-110">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="c8fb3-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|<span data-ttu-id="c8fb3-111">Especifica o comprimento máximo de um cabeçalho de resposta, em kilobytes.</span><span class="sxs-lookup"><span data-stu-id="c8fb3-111">Specifies the maximum length of a response header, in kilobytes.</span></span> <span data-ttu-id="c8fb3-112">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="c8fb3-112">The default is 64.</span></span> <span data-ttu-id="c8fb3-113">Um valor de-1 indica que nenhum limite de tamanho será imposto nos cabeçalhos de resposta.</span><span class="sxs-lookup"><span data-stu-id="c8fb3-113">A value of -1 indicates that no size limit will be imposed on the response headers.</span></span>|  
|`maximumErrorResponseLength`|<span data-ttu-id="c8fb3-114">Especifica o comprimento máximo de uma resposta de erro, em quilobytes.</span><span class="sxs-lookup"><span data-stu-id="c8fb3-114">Specifies the maximum length of an error response, in kilobytes.</span></span> <span data-ttu-id="c8fb3-115">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="c8fb3-115">The default is 64.</span></span> <span data-ttu-id="c8fb3-116">Um valor de-1 indica que nenhum limite de tamanho será imposto sobre a resposta de erro.</span><span class="sxs-lookup"><span data-stu-id="c8fb3-116">A value of -1 indicates that no size limit will be imposed on the error response.</span></span>|  
|`maximumUnauthorizedUploadLength`|<span data-ttu-id="c8fb3-117">Especifica o comprimento máximo de um carregamento em resposta a um código de erro não autorizado, em bytes.</span><span class="sxs-lookup"><span data-stu-id="c8fb3-117">Specifies the maximum length of an upload in response to an unauthorized error code, in bytes.</span></span> <span data-ttu-id="c8fb3-118">O padrão é -1.</span><span class="sxs-lookup"><span data-stu-id="c8fb3-118">The default is -1.</span></span> <span data-ttu-id="c8fb3-119">Um valor de-1 indica que nenhum limite de tamanho será imposto no carregamento.</span><span class="sxs-lookup"><span data-stu-id="c8fb3-119">A value of -1 indicates that no size limit will be imposed on the upload.</span></span>|  
|`useUnsafeHeaderParsing`|<span data-ttu-id="c8fb3-120">Especifica se a análise de cabeçalho não seguro está habilitada.</span><span class="sxs-lookup"><span data-stu-id="c8fb3-120">Specifies whether unsafe header parsing is enabled.</span></span> <span data-ttu-id="c8fb3-121">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="c8fb3-121">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c8fb3-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c8fb3-122">Child Elements</span></span>  
 <span data-ttu-id="c8fb3-123">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c8fb3-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c8fb3-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c8fb3-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c8fb3-125">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="c8fb3-125">**Element**</span></span>|<span data-ttu-id="c8fb3-126">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="c8fb3-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c8fb3-127">configurações</span><span class="sxs-lookup"><span data-stu-id="c8fb3-127">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="c8fb3-128">Configura as opções de rede básicaspara o namespace <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="c8fb3-128">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8fb3-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="c8fb3-129">Remarks</span></span>  
 <span data-ttu-id="c8fb3-130">Por padrão, o .NET Framework impõe estritamente a RFC 2616 para análise de URI.</span><span class="sxs-lookup"><span data-stu-id="c8fb3-130">By default, the .NET Framework strictly enforces RFC 2616 for URI parsing.</span></span> <span data-ttu-id="c8fb3-131">Algumas respostas do servidor podem incluir caracteres de controle em campos proibidos, o que fará com que o <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> método gere um <xref:System.Net.WebException> .</span><span class="sxs-lookup"><span data-stu-id="c8fb3-131">Some server responses may include control characters in prohibited fields, which will cause the <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> method to throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="c8fb3-132">Se **UseUnsafeHeaderParsing** for definido como **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> o não será lançado nesse caso; no entanto, seu aplicativo ficará vulnerável a várias formas de ataques de análise de URI.</span><span class="sxs-lookup"><span data-stu-id="c8fb3-132">If **useUnsafeHeaderParsing** is set to **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> will not throw in this case; however, your application will be vulnerable to several forms of URI parsing attacks.</span></span> <span data-ttu-id="c8fb3-133">A melhor solução é alterar o servidor para que a resposta não inclua caracteres de controle.</span><span class="sxs-lookup"><span data-stu-id="c8fb3-133">The best solution is to change the server so that the response does not include control characters.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c8fb3-134">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="c8fb3-134">Configuration Files</span></span>  
 <span data-ttu-id="c8fb3-135">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="c8fb3-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8fb3-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c8fb3-136">Example</span></span>  
 <span data-ttu-id="c8fb3-137">O exemplo a seguir mostra como especificar um comprimento de cabeçalho máximo de tamanho maior que normal.</span><span class="sxs-lookup"><span data-stu-id="c8fb3-137">The following example shows how to specify a larger than normal maximum header length.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpWebRequest  
        maximumResponseHeadersLength="128"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c8fb3-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="c8fb3-138">See also</span></span>

- <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>
- [<span data-ttu-id="c8fb3-139">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="c8fb3-139">Network Settings Schema</span></span>](index.md)
