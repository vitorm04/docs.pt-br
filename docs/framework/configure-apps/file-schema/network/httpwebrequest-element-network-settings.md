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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087450"
---
# <a name="httpwebrequest-element-network-settings"></a><span data-ttu-id="a70f5-102">Elemento \<httpWebRequest> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="a70f5-102">\<httpWebRequest> Element (Network Settings)</span></span>
<span data-ttu-id="a70f5-103">Personaliza os parâmetros de solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="a70f5-103">Customizes Web request parameters.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpWebRequest>**

## <a name="syntax"></a><span data-ttu-id="a70f5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a70f5-104">Syntax</span></span>  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a70f5-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a70f5-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a70f5-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a70f5-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a70f5-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="a70f5-107">Attributes</span></span>  
  
|<span data-ttu-id="a70f5-108">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="a70f5-108">**Attribute**</span></span>|<span data-ttu-id="a70f5-109">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="a70f5-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|<span data-ttu-id="a70f5-110">Especifica o comprimento máximo de um cabeçalho de resposta, em kilobytes.</span><span class="sxs-lookup"><span data-stu-id="a70f5-110">Specifies the maximum length of a response header, in kilobytes.</span></span> <span data-ttu-id="a70f5-111">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="a70f5-111">The default is 64.</span></span> <span data-ttu-id="a70f5-112">Um valor de-1 indica que nenhum limite de tamanho será imposto nos cabeçalhos de resposta.</span><span class="sxs-lookup"><span data-stu-id="a70f5-112">A value of -1 indicates that no size limit will be imposed on the response headers.</span></span>|  
|`maximumErrorResponseLength`|<span data-ttu-id="a70f5-113">Especifica o comprimento máximo de uma resposta de erro, em quilobytes.</span><span class="sxs-lookup"><span data-stu-id="a70f5-113">Specifies the maximum length of an error response, in kilobytes.</span></span> <span data-ttu-id="a70f5-114">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="a70f5-114">The default is 64.</span></span> <span data-ttu-id="a70f5-115">Um valor de-1 indica que nenhum limite de tamanho será imposto sobre a resposta de erro.</span><span class="sxs-lookup"><span data-stu-id="a70f5-115">A value of -1 indicates that no size limit will be imposed on the error response.</span></span>|  
|`maximumUnauthorizedUploadLength`|<span data-ttu-id="a70f5-116">Especifica o comprimento máximo de um carregamento em resposta a um código de erro não autorizado, em bytes.</span><span class="sxs-lookup"><span data-stu-id="a70f5-116">Specifies the maximum length of an upload in response to an unauthorized error code, in bytes.</span></span> <span data-ttu-id="a70f5-117">O padrão é -1.</span><span class="sxs-lookup"><span data-stu-id="a70f5-117">The default is -1.</span></span> <span data-ttu-id="a70f5-118">Um valor de-1 indica que nenhum limite de tamanho será imposto no carregamento.</span><span class="sxs-lookup"><span data-stu-id="a70f5-118">A value of -1 indicates that no size limit will be imposed on the upload.</span></span>|  
|`useUnsafeHeaderParsing`|<span data-ttu-id="a70f5-119">Especifica se a análise de cabeçalho não seguro está habilitada.</span><span class="sxs-lookup"><span data-stu-id="a70f5-119">Specifies whether unsafe header parsing is enabled.</span></span> <span data-ttu-id="a70f5-120">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="a70f5-120">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a70f5-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a70f5-121">Child Elements</span></span>  
 <span data-ttu-id="a70f5-122">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a70f5-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a70f5-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a70f5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a70f5-124">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="a70f5-124">**Element**</span></span>|<span data-ttu-id="a70f5-125">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="a70f5-125">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a70f5-126">configurações</span><span class="sxs-lookup"><span data-stu-id="a70f5-126">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="a70f5-127">Configura as opções de rede básicaspara o namespace <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="a70f5-127">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a70f5-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="a70f5-128">Remarks</span></span>  
 <span data-ttu-id="a70f5-129">Por padrão, o .NET Framework impõe estritamente a RFC 2616 para análise de URI.</span><span class="sxs-lookup"><span data-stu-id="a70f5-129">By default, the .NET Framework strictly enforces RFC 2616 for URI parsing.</span></span> <span data-ttu-id="a70f5-130">Algumas respostas do servidor podem incluir caracteres de controle em campos proibidos, o que fará com que o <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> método gere um <xref:System.Net.WebException> .</span><span class="sxs-lookup"><span data-stu-id="a70f5-130">Some server responses may include control characters in prohibited fields, which will cause the <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> method to throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="a70f5-131">Se **UseUnsafeHeaderParsing** for definido como **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> o não será lançado nesse caso; no entanto, seu aplicativo ficará vulnerável a várias formas de ataques de análise de URI.</span><span class="sxs-lookup"><span data-stu-id="a70f5-131">If **useUnsafeHeaderParsing** is set to **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> will not throw in this case; however, your application will be vulnerable to several forms of URI parsing attacks.</span></span> <span data-ttu-id="a70f5-132">A melhor solução é alterar o servidor para que a resposta não inclua caracteres de controle.</span><span class="sxs-lookup"><span data-stu-id="a70f5-132">The best solution is to change the server so that the response does not include control characters.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a70f5-133">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="a70f5-133">Configuration Files</span></span>  
 <span data-ttu-id="a70f5-134">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="a70f5-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a70f5-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a70f5-135">Example</span></span>  
 <span data-ttu-id="a70f5-136">O exemplo a seguir mostra como especificar um comprimento de cabeçalho máximo de tamanho maior que normal.</span><span class="sxs-lookup"><span data-stu-id="a70f5-136">The following example shows how to specify a larger than normal maximum header length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a70f5-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="a70f5-137">See also</span></span>

- <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>
- [<span data-ttu-id="a70f5-138">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="a70f5-138">Network Settings Schema</span></span>](index.md)
