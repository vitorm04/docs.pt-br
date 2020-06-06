---
title: Elemento <add> para webRequestModules (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <webRequestModules>, add element
- webRequestModules, add element
- add element, webRequestModules
- <add> element, webRequestModules
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
ms.openlocfilehash: f4edce948033478aab59a2aff61abadc55a327ce
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155018"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="c1f15-102">Elemento \<add> para webRequestModules (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="c1f15-102">\<add> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="c1f15-103">Adiciona um módulo de solicitação da Web personalizado ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c1f15-103">Adds a custom Web request module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="c1f15-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c1f15-104">Syntax</span></span>  
  
```xml  
<add
  prefix="URI prefix"
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1f15-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c1f15-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c1f15-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c1f15-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1f15-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="c1f15-107">Attributes</span></span>  
  
|<span data-ttu-id="c1f15-108">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="c1f15-108">**Attribute**</span></span>|<span data-ttu-id="c1f15-109">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="c1f15-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="c1f15-110">O prefixo de URI para solicitações tratadas por este módulo de solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="c1f15-110">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="c1f15-111">O nome do tipo totalmente qualificado (indicado pela <xref:System.Type.FullName%2A> Propriedade) e o nome do assembly (indicado pela <xref:System.Reflection.Assembly.FullName%2A> Propriedade), separados por uma vírgula, que implementa esse módulo de solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="c1f15-111">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c1f15-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c1f15-112">Child Elements</span></span>  
 <span data-ttu-id="c1f15-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c1f15-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c1f15-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c1f15-114">Parent Elements</span></span>  
  
|<span data-ttu-id="c1f15-115">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="c1f15-115">**Element**</span></span>|<span data-ttu-id="c1f15-116">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="c1f15-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c1f15-117">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="c1f15-117">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="c1f15-118">Especifica os módulos a serem usados para solicitar informações de hosts de rede.</span><span class="sxs-lookup"><span data-stu-id="c1f15-118">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1f15-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="c1f15-119">Remarks</span></span>  
 <span data-ttu-id="c1f15-120">O `prefix` atributo define o prefixo de URI que usa o módulo de solicitação da Web especificado.</span><span class="sxs-lookup"><span data-stu-id="c1f15-120">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="c1f15-121">Os módulos de solicitação da Web normalmente são registrados para lidar com um protocolo específico, como HTTP ou FTP, mas podem ser registrados para lidar com uma solicitação para um servidor ou caminho específico em um servidor.</span><span class="sxs-lookup"><span data-stu-id="c1f15-121">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="c1f15-122">O módulo de solicitação da Web é criado quando um prefixo de correspondência de URI é passado para o <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="c1f15-122">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="c1f15-123">O valor do `prefix` atributo deve ser os caracteres à esquerda de um URI válido.</span><span class="sxs-lookup"><span data-stu-id="c1f15-123">The value for the `prefix` attribute should be the leading characters of a valid URI.</span></span> <span data-ttu-id="c1f15-124">Por exemplo, `http` ou `http://www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="c1f15-124">For example, `http` or `http://www.contoso.com`.</span></span>
  
 <span data-ttu-id="c1f15-125">O valor do `type` atributo deve ser um nome de tipo válido e um nome de assembly correspondente, separados por uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="c1f15-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>
  
## <a name="configuration-files"></a><span data-ttu-id="c1f15-126">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="c1f15-126">Configuration Files</span></span>  
 <span data-ttu-id="c1f15-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="c1f15-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1f15-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c1f15-128">Example</span></span>  
 <span data-ttu-id="c1f15-129">O exemplo a seguir registra um módulo de solicitação da Web personalizado para HTTP.</span><span class="sxs-lookup"><span data-stu-id="c1f15-129">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="c1f15-130">Você deve substituir os valores de Version e PublicKeyToken pelos valores corretos para o módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="c1f15-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c1f15-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="c1f15-131">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="c1f15-132">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="c1f15-132">Network Settings Schema</span></span>](index.md)
