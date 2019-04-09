---
title: <httpWebRequest> (Configurações de rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
ms.openlocfilehash: 722b2f726c9085f6dee6bad82044da3011b98702
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169293"
---
# <a name="httpwebrequest-element-network-settings"></a><span data-ttu-id="aa1ec-102">\<httpWebRequest > (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="aa1ec-102">\<httpWebRequest> Element (Network Settings)</span></span>
<span data-ttu-id="aa1ec-103">Personaliza os parâmetros de solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="aa1ec-103">Customizes Web request parameters.</span></span>  
  
 <span data-ttu-id="aa1ec-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="aa1ec-104">\<configuration></span></span>  
<span data-ttu-id="aa1ec-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="aa1ec-105">\<system.net></span></span>  
<span data-ttu-id="aa1ec-106">\<Configurações ></span><span class="sxs-lookup"><span data-stu-id="aa1ec-106">\<settings></span></span>  
<span data-ttu-id="aa1ec-107">\<httpWebRequest></span><span class="sxs-lookup"><span data-stu-id="aa1ec-107">\<httpWebRequest></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa1ec-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aa1ec-108">Syntax</span></span>  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa1ec-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="aa1ec-109">Attributes and Elements</span></span>  
 <span data-ttu-id="aa1ec-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="aa1ec-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa1ec-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="aa1ec-111">Attributes</span></span>  
  
|**<span data-ttu-id="aa1ec-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="aa1ec-112">Attribute</span></span>**|**<span data-ttu-id="aa1ec-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="aa1ec-113">Description</span></span>**|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|<span data-ttu-id="aa1ec-114">Especifica o comprimento máximo de um cabeçalho de resposta, em quilobytes.</span><span class="sxs-lookup"><span data-stu-id="aa1ec-114">Specifies the maximum length of a response header, in kilobytes.</span></span> <span data-ttu-id="aa1ec-115">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="aa1ec-115">The default is 64.</span></span> <span data-ttu-id="aa1ec-116">Um valor de -1 indica que nenhum limite de tamanho será imposto nos cabeçalhos de resposta.</span><span class="sxs-lookup"><span data-stu-id="aa1ec-116">A value of -1 indicates that no size limit will be imposed on the response headers.</span></span>|  
|`maximumErrorResponseLength`|<span data-ttu-id="aa1ec-117">Especifica o comprimento máximo de uma resposta de erro, em quilobytes.</span><span class="sxs-lookup"><span data-stu-id="aa1ec-117">Specifies the maximum length of an error response, in kilobytes.</span></span> <span data-ttu-id="aa1ec-118">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="aa1ec-118">The default is 64.</span></span> <span data-ttu-id="aa1ec-119">Um valor de -1 indica que nenhum limite de tamanho será imposto na resposta de erro.</span><span class="sxs-lookup"><span data-stu-id="aa1ec-119">A value of -1 indicates that no size limit will be imposed on the error response.</span></span>|  
|`maximumUnauthorizedUploadLength`|<span data-ttu-id="aa1ec-120">Especifica o comprimento máximo de um upload em resposta a um código de erro não autorizado, em bytes.</span><span class="sxs-lookup"><span data-stu-id="aa1ec-120">Specifies the maximum length of an upload in response to an unauthorized error code, in bytes.</span></span> <span data-ttu-id="aa1ec-121">O padrão é -1.</span><span class="sxs-lookup"><span data-stu-id="aa1ec-121">The default is -1.</span></span> <span data-ttu-id="aa1ec-122">Um valor de -1 indica que nenhum limite de tamanho será imposto durante o upload.</span><span class="sxs-lookup"><span data-stu-id="aa1ec-122">A value of -1 indicates that no size limit will be imposed on the upload.</span></span>|  
|`useUnsafeHeaderParsing`|<span data-ttu-id="aa1ec-123">Especifica se a análise de cabeçalho não seguro está habilitada.</span><span class="sxs-lookup"><span data-stu-id="aa1ec-123">Specifies whether unsafe header parsing is enabled.</span></span> <span data-ttu-id="aa1ec-124">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="aa1ec-124">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aa1ec-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="aa1ec-125">Child Elements</span></span>  
 <span data-ttu-id="aa1ec-126">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="aa1ec-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aa1ec-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="aa1ec-127">Parent Elements</span></span>  
  
|**<span data-ttu-id="aa1ec-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="aa1ec-128">Element</span></span>**|**<span data-ttu-id="aa1ec-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="aa1ec-129">Description</span></span>**|  
|-----------------|---------------------|  
|[<span data-ttu-id="aa1ec-130">configurações</span><span class="sxs-lookup"><span data-stu-id="aa1ec-130">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="aa1ec-131">Configura as opções de rede básicaspara o namespace <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="aa1ec-131">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa1ec-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="aa1ec-132">Remarks</span></span>  
 <span data-ttu-id="aa1ec-133">Por padrão, o .NET Framework impõe rigidamente RFC 2616 para análise de URI.</span><span class="sxs-lookup"><span data-stu-id="aa1ec-133">By default, the .NET Framework strictly enforces RFC 2616 for URI parsing.</span></span> <span data-ttu-id="aa1ec-134">Algumas respostas do servidor podem incluir caracteres de controle nos campos proibidos, que fará com que o <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> método para lançar um <xref:System.Net.WebException>.</span><span class="sxs-lookup"><span data-stu-id="aa1ec-134">Some server responses may include control characters in prohibited fields, which will cause the <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> method to throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="aa1ec-135">Se **useUnsafeHeaderParsing** é definido como **verdadeiro**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> não lançará neste caso, no entanto, seu aplicativo estará vulnerável a diversas formas de ataques de análise de URI.</span><span class="sxs-lookup"><span data-stu-id="aa1ec-135">If **useUnsafeHeaderParsing** is set to **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> will not throw in this case; however, your application will be vulnerable to several forms of URI parsing attacks.</span></span> <span data-ttu-id="aa1ec-136">A melhor solução é alterar o servidor para que a resposta não inclui caracteres de controle.</span><span class="sxs-lookup"><span data-stu-id="aa1ec-136">The best solution is to change the server so that the response does not include control characters.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="aa1ec-137">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="aa1ec-137">Configuration Files</span></span>  
 <span data-ttu-id="aa1ec-138">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="aa1ec-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa1ec-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aa1ec-139">Example</span></span>  
 <span data-ttu-id="aa1ec-140">O exemplo a seguir mostra como especificar uma maior que o tamanho máximo do cabeçalho normal.</span><span class="sxs-lookup"><span data-stu-id="aa1ec-140">The following example shows how to specify a larger than normal maximum header length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aa1ec-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa1ec-141">See also</span></span>

- <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>
- [<span data-ttu-id="aa1ec-142">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="aa1ec-142">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
