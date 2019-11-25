---
title: Elemento <httpWebRequest> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
ms.openlocfilehash: d33dadc14510feb00e05ca557b507b0cf8fa0dd0
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087450"
---
# <a name="httpwebrequest-element-network-settings"></a><span data-ttu-id="3e4df-102">\<o elemento > httpWebRequest (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="3e4df-102">\<httpWebRequest> Element (Network Settings)</span></span>
<span data-ttu-id="3e4df-103">Personaliza os parâmetros de solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="3e4df-103">Customizes Web request parameters.</span></span>  

<span data-ttu-id="3e4df-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3e4df-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3e4df-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="3e4df-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="3e4df-106">&nbsp;&nbsp;&nbsp;&nbsp;\<[**configurações**](settings-element-network-settings.md) ></span><span class="sxs-lookup"><span data-stu-id="3e4df-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\</span></span>
<span data-ttu-id="3e4df-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**httpWebRequest >**</span><span class="sxs-lookup"><span data-stu-id="3e4df-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpWebRequest>**</span></span>

## <a name="syntax"></a><span data-ttu-id="3e4df-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e4df-108">Syntax</span></span>  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e4df-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3e4df-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3e4df-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3e4df-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e4df-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="3e4df-111">Attributes</span></span>  
  
|<span data-ttu-id="3e4df-112">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="3e4df-112">**Attribute**</span></span>|<span data-ttu-id="3e4df-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="3e4df-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|<span data-ttu-id="3e4df-114">Especifica o comprimento máximo de um cabeçalho de resposta, em kilobytes.</span><span class="sxs-lookup"><span data-stu-id="3e4df-114">Specifies the maximum length of a response header, in kilobytes.</span></span> <span data-ttu-id="3e4df-115">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="3e4df-115">The default is 64.</span></span> <span data-ttu-id="3e4df-116">Um valor de-1 indica que nenhum limite de tamanho será imposto nos cabeçalhos de resposta.</span><span class="sxs-lookup"><span data-stu-id="3e4df-116">A value of -1 indicates that no size limit will be imposed on the response headers.</span></span>|  
|`maximumErrorResponseLength`|<span data-ttu-id="3e4df-117">Especifica o comprimento máximo de uma resposta de erro, em quilobytes.</span><span class="sxs-lookup"><span data-stu-id="3e4df-117">Specifies the maximum length of an error response, in kilobytes.</span></span> <span data-ttu-id="3e4df-118">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="3e4df-118">The default is 64.</span></span> <span data-ttu-id="3e4df-119">Um valor de-1 indica que nenhum limite de tamanho será imposto sobre a resposta de erro.</span><span class="sxs-lookup"><span data-stu-id="3e4df-119">A value of -1 indicates that no size limit will be imposed on the error response.</span></span>|  
|`maximumUnauthorizedUploadLength`|<span data-ttu-id="3e4df-120">Especifica o comprimento máximo de um carregamento em resposta a um código de erro não autorizado, em bytes.</span><span class="sxs-lookup"><span data-stu-id="3e4df-120">Specifies the maximum length of an upload in response to an unauthorized error code, in bytes.</span></span> <span data-ttu-id="3e4df-121">O padrão é -1.</span><span class="sxs-lookup"><span data-stu-id="3e4df-121">The default is -1.</span></span> <span data-ttu-id="3e4df-122">Um valor de-1 indica que nenhum limite de tamanho será imposto no carregamento.</span><span class="sxs-lookup"><span data-stu-id="3e4df-122">A value of -1 indicates that no size limit will be imposed on the upload.</span></span>|  
|`useUnsafeHeaderParsing`|<span data-ttu-id="3e4df-123">Especifica se a análise de cabeçalho não seguro está habilitada.</span><span class="sxs-lookup"><span data-stu-id="3e4df-123">Specifies whether unsafe header parsing is enabled.</span></span> <span data-ttu-id="3e4df-124">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="3e4df-124">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e4df-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3e4df-125">Child Elements</span></span>  
 <span data-ttu-id="3e4df-126">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3e4df-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3e4df-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3e4df-127">Parent Elements</span></span>  
  
|<span data-ttu-id="3e4df-128">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="3e4df-128">**Element**</span></span>|<span data-ttu-id="3e4df-129">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="3e4df-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3e4df-130">Configurações</span><span class="sxs-lookup"><span data-stu-id="3e4df-130">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="3e4df-131">Configura as opções de rede básicaspara o namespace <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="3e4df-131">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e4df-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="3e4df-132">Remarks</span></span>  
 <span data-ttu-id="3e4df-133">Por padrão, o .NET Framework impõe estritamente a RFC 2616 para análise de URI.</span><span class="sxs-lookup"><span data-stu-id="3e4df-133">By default, the .NET Framework strictly enforces RFC 2616 for URI parsing.</span></span> <span data-ttu-id="3e4df-134">Algumas respostas do servidor podem incluir caracteres de controle em campos proibidos, o que fará com que o método <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> gere um <xref:System.Net.WebException>.</span><span class="sxs-lookup"><span data-stu-id="3e4df-134">Some server responses may include control characters in prohibited fields, which will cause the <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> method to throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="3e4df-135">Se **UseUnsafeHeaderParsing** for definido como **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> não será lançada nesse caso; no entanto, seu aplicativo ficará vulnerável a várias formas de ataques de análise de URI.</span><span class="sxs-lookup"><span data-stu-id="3e4df-135">If **useUnsafeHeaderParsing** is set to **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> will not throw in this case; however, your application will be vulnerable to several forms of URI parsing attacks.</span></span> <span data-ttu-id="3e4df-136">A melhor solução é alterar o servidor para que a resposta não inclua caracteres de controle.</span><span class="sxs-lookup"><span data-stu-id="3e4df-136">The best solution is to change the server so that the response does not include control characters.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="3e4df-137">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="3e4df-137">Configuration Files</span></span>  
 <span data-ttu-id="3e4df-138">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="3e4df-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e4df-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3e4df-139">Example</span></span>  
 <span data-ttu-id="3e4df-140">O exemplo a seguir mostra como especificar um comprimento de cabeçalho máximo de tamanho maior que normal.</span><span class="sxs-lookup"><span data-stu-id="3e4df-140">The following example shows how to specify a larger than normal maximum header length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3e4df-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e4df-141">See also</span></span>

- <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>
- [<span data-ttu-id="3e4df-142">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="3e4df-142">Network Settings Schema</span></span>](index.md)
