---
title: Elemento <iriParsing> (Configurações de URI)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: ec2610e47957d5560bc7f51e0641afc9ba60c814
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158884"
---
# <a name="iriparsing-element-uri-settings"></a><span data-ttu-id="e784e-102">Elemento \<iriParsing> (Configurações de URI)</span><span class="sxs-lookup"><span data-stu-id="e784e-102">\<iriParsing> Element (Uri Settings)</span></span>

<span data-ttu-id="e784e-103">Especifica se a análise de IRI (Identificador de Recurso Internacional) é aplicada a um <xref:System.Uri> e se as regras de análise de IRI devem ser aplicada.</span><span class="sxs-lookup"><span data-stu-id="e784e-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<iriParsing>**  
  
## <a name="syntax"></a><span data-ttu-id="e784e-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e784e-104">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e784e-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e784e-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e784e-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e784e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e784e-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="e784e-107">Attributes</span></span>  
  
|<span data-ttu-id="e784e-108">**Element**</span><span class="sxs-lookup"><span data-stu-id="e784e-108">**Element**</span></span>|<span data-ttu-id="e784e-109">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="e784e-109">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="e784e-110">Especifica se a análise de IRI está habilitada.</span><span class="sxs-lookup"><span data-stu-id="e784e-110">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="e784e-111">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="e784e-111">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e784e-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e784e-112">Child Elements</span></span>  

 <span data-ttu-id="e784e-113">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e784e-113">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e784e-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e784e-114">Parent Elements</span></span>  
  
|<span data-ttu-id="e784e-115">**Element**</span><span class="sxs-lookup"><span data-stu-id="e784e-115">**Element**</span></span>|<span data-ttu-id="e784e-116">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="e784e-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e784e-117">uri</span><span class="sxs-lookup"><span data-stu-id="e784e-117">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="e784e-118">Contém configurações que especificam como o .NET Framework trata os endereços da Web expressos usando URIs (identificadores de recursos uniformes).</span><span class="sxs-lookup"><span data-stu-id="e784e-118">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e784e-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="e784e-119">Remarks</span></span>  

 <span data-ttu-id="e784e-120">A <xref:System.Uri> classe existente foi estendida no .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="e784e-120">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="e784e-121">3,0 SP1 e 2,0 SP1 para fornecer suporte para IRI (identificadores de recursos internacionais) e IDNs (nomes de domínio internacionalizados).</span><span class="sxs-lookup"><span data-stu-id="e784e-121">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="e784e-122">Os usuários atuais não verão nenhuma alteração do comportamento .NET Framework 2,0, a menos que eles especificamente habilitem o suporte a IRI e IDN.</span><span class="sxs-lookup"><span data-stu-id="e784e-122">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="e784e-123">Isso garante a compatibilidade do aplicativo com versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e784e-123">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="e784e-124">Para habilitar o suporte para IRI, as duas alterações a seguir são necessárias:</span><span class="sxs-lookup"><span data-stu-id="e784e-124">To enable support for IRI, the following two changes are required:</span></span>  
  
1. <span data-ttu-id="e784e-125">Adicione a seguinte linha ao arquivo de machine.config no diretório .NET Framework 2,0</span><span class="sxs-lookup"><span data-stu-id="e784e-125">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="e784e-126">Especifique se as regras de análise de IRI devem ser aplicadas.</span><span class="sxs-lookup"><span data-stu-id="e784e-126">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="e784e-127">Isso pode ser feito no arquivo machine.config ou em app.config.</span><span class="sxs-lookup"><span data-stu-id="e784e-127">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="e784e-128">Habilitar a análise de IRI (iriParsing Enabled = `true` ) fará a normalização e a verificação de caracteres de acordo com as regras de IRI mais recentes no RFC 3987.</span><span class="sxs-lookup"><span data-stu-id="e784e-128">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="e784e-129">O valor padrão é `false` e fará a normalização e a verificação de caracteres de acordo com rfc 2396 e rfc 3986 (para literais IPv6).</span><span class="sxs-lookup"><span data-stu-id="e784e-129">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="e784e-130">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="e784e-130">Configuration Files</span></span>  

 <span data-ttu-id="e784e-131">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="e784e-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e784e-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e784e-132">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="e784e-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="e784e-133">Description</span></span>  

 <span data-ttu-id="e784e-134">O exemplo a seguir mostra uma configuração usada pela <xref:System.Uri> classe para dar suporte a análise de IRI e nomes IDN.</span><span class="sxs-lookup"><span data-stu-id="e784e-134">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e784e-135">Código</span><span class="sxs-lookup"><span data-stu-id="e784e-135">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e784e-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="e784e-136">See also</span></span>

- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="e784e-137">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="e784e-137">Network Settings Schema</span></span>](index.md)
