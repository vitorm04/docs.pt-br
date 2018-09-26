---
title: '&lt;IDN&gt; (configurações de Uri)'
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 1537c17cb3c16beeb41cfaa4103e0664e93facc7
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47170594"
---
# <a name="ltidngt-element-uri-settings"></a><span data-ttu-id="ef1a3-102">&lt;IDN&gt; (configurações de Uri)</span><span class="sxs-lookup"><span data-stu-id="ef1a3-102">&lt;idn&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="ef1a3-103">Especifica se a análise de nome de domínio internacionalizado (IDN) é aplicado a um nome de domínio.</span><span class="sxs-lookup"><span data-stu-id="ef1a3-103">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="ef1a3-104">Hierarquia de esquema</span><span class="sxs-lookup"><span data-stu-id="ef1a3-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="ef1a3-105">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="ef1a3-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="ef1a3-106">\<URI > (configurações de Uri)</span><span class="sxs-lookup"><span data-stu-id="ef1a3-106">\<Uri> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [<span data-ttu-id="ef1a3-107">\<IDN ></span><span class="sxs-lookup"><span data-stu-id="ef1a3-107">\<idn></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="ef1a3-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ef1a3-108">Syntax</span></span>  
  
```xml  
<idn  
  enabled="All|AllExceptIntranet|None"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef1a3-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ef1a3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ef1a3-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ef1a3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef1a3-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="ef1a3-111">Attributes</span></span>  
  
|<span data-ttu-id="ef1a3-112">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="ef1a3-112">**Element**</span></span>|<span data-ttu-id="ef1a3-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="ef1a3-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="ef1a3-114">Especifica que se a análise de nome de domínio internacionalizado (IDN) for aplicado a um nome de domínio o valor padrão é none.</span><span class="sxs-lookup"><span data-stu-id="ef1a3-114">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name The default value is none.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ef1a3-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ef1a3-115">Child Elements</span></span>  
 <span data-ttu-id="ef1a3-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="ef1a3-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ef1a3-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ef1a3-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ef1a3-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="ef1a3-118">**Element**</span></span>|<span data-ttu-id="ef1a3-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="ef1a3-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ef1a3-120">URI</span><span class="sxs-lookup"><span data-stu-id="ef1a3-120">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="ef1a3-121">Contém configurações que especificam como o .NET Framework controla endereços da web expressados usando identificadores de recurso uniformes (URIs).</span><span class="sxs-lookup"><span data-stu-id="ef1a3-121">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef1a3-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="ef1a3-122">Remarks</span></span>  
 <span data-ttu-id="ef1a3-123">Existente <xref:System.Uri> classe foi estendido no .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="ef1a3-123">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="ef1a3-124">3.0 SP1 e 2.0 SP1 com suporte para identificadores de recursos internacionais (IRI) e nomes de domínio internacionalizado (IDN).</span><span class="sxs-lookup"><span data-stu-id="ef1a3-124">3.0 SP1, and 2.0 SP1 with support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="ef1a3-125">Os usuários atuais não verão qualquer mudança do comportamento do .NET Framework 2.0, a menos que eles especificamente habilitarem IRI e IDN dão suporte.</span><span class="sxs-lookup"><span data-stu-id="ef1a3-125">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="ef1a3-126">Isso garante a compatibilidade do aplicativo com versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ef1a3-126">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="ef1a3-127">Para habilitar o suporte IRI, duas alterações a seguir são necessárias:</span><span class="sxs-lookup"><span data-stu-id="ef1a3-127">To enable support for IRI, the following two changes are required:</span></span>  
  
1.  <span data-ttu-id="ef1a3-128">Adicione a seguinte linha ao arquivo Machine. config no diretório do .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="ef1a3-128">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  <span data-ttu-id="ef1a3-129">Especifique se deseja que a análise de nome de domínio internacionalizado (IDN) aplicada ao nome de domínio e se as regras de análise do IRI deve ser aplicado.</span><span class="sxs-lookup"><span data-stu-id="ef1a3-129">Specify whether you want Internationalized Domain Name (IDN) parsing applied to the domain name and whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="ef1a3-130">Isso pode ser feito no arquivo machine.config ou em app.config.</span><span class="sxs-lookup"><span data-stu-id="ef1a3-130">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="ef1a3-131">Há três valores possíveis para IDN, dependendo dos servidores DNS que são usados:</span><span class="sxs-lookup"><span data-stu-id="ef1a3-131">There are three possible values for IDN depending on the DNS servers that are used:</span></span>  
  
-   <span data-ttu-id="ef1a3-132">IDN habilitado = All</span><span class="sxs-lookup"><span data-stu-id="ef1a3-132">idn enabled = All</span></span>  
  
     <span data-ttu-id="ef1a3-133">Esse valor converterá todos os nomes de domínio Unicode em seus equivalentes do Punycode (nomes IDN).</span><span class="sxs-lookup"><span data-stu-id="ef1a3-133">This value will convert any Unicode domain names to their Punycode equivalents (IDN names).</span></span>  
  
-   <span data-ttu-id="ef1a3-134">IDN habilitado = AllExceptIntranet</span><span class="sxs-lookup"><span data-stu-id="ef1a3-134">idn enabled = AllExceptIntranet</span></span>  
  
     <span data-ttu-id="ef1a3-135">Esse valor converterá todos os nomes de domínio Unicode não está na Intranet local para usar os equivalentes do Punycode (nomes IDN).</span><span class="sxs-lookup"><span data-stu-id="ef1a3-135">This value will convert all Unicode domain names not on the local Intranet to use the Punycode equivalents (IDN names).</span></span> <span data-ttu-id="ef1a3-136">Nesse caso, para manipular nomes internacionais na Intranet local, os servidores DNS que são usados para a Intranet devem dar suporte a resolução de nomes do Unicode.</span><span class="sxs-lookup"><span data-stu-id="ef1a3-136">In this case to handle international names on the local Intranet, the DNS servers that are used for the Intranet should support Unicode name resolution.</span></span>  
  
-   <span data-ttu-id="ef1a3-137">IDN habilitado = nenhum</span><span class="sxs-lookup"><span data-stu-id="ef1a3-137">idn enabled = None</span></span>  
  
     <span data-ttu-id="ef1a3-138">Esse valor não converterá nenhum nome de domínio Unicode para usar o Punycode.</span><span class="sxs-lookup"><span data-stu-id="ef1a3-138">This value will not convert any Unicode domain names to use Punycode.</span></span> <span data-ttu-id="ef1a3-139">Isso é o valor padrão que é consistente com o comportamento do .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="ef1a3-139">This is the default value which is consistent with the .NET Framework 2.0 behaviour.</span></span>  
  
 <span data-ttu-id="ef1a3-140">Habilitar o IDN converterá todos os rótulos Unicode de um nome de domínio para seus equivalentes em Punycode.</span><span class="sxs-lookup"><span data-stu-id="ef1a3-140">Enabling IDN will convert all Unicode labels in a domain name to their Punycode equivalents.</span></span> <span data-ttu-id="ef1a3-141">Os nomes Punycode contêm apenas caracteres ASCII e sempre começam com o prefixo xn--.</span><span class="sxs-lookup"><span data-stu-id="ef1a3-141">Punycode names contain only ASCII characters and always start with the xn-- prefix.</span></span> <span data-ttu-id="ef1a3-142">A razão para isso é dar suporte a servidores DNS existentes na Internet, pois a maioria dos servidores DNS dá suporte somente a caracteres ASCII (consulte RFC 3940).</span><span class="sxs-lookup"><span data-stu-id="ef1a3-142">The reason for this is to support existing DNS servers on the Internet, since most DNS servers only support ASCII characters (see RFC 3940).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="ef1a3-143">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="ef1a3-143">Configuration Files</span></span>  
 <span data-ttu-id="ef1a3-144">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="ef1a3-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef1a3-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ef1a3-145">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ef1a3-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef1a3-146">Description</span></span>  
 <span data-ttu-id="ef1a3-147">O exemplo a seguir mostra uma configuração usada pelo <xref:System.Uri> classe para dar suporte à análise de IRI e nomes IDN.</span><span class="sxs-lookup"><span data-stu-id="ef1a3-147">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ef1a3-148">Código</span><span class="sxs-lookup"><span data-stu-id="ef1a3-148">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef1a3-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef1a3-149">See Also</span></span>  
 <xref:System.Configuration.IdnElement?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 [<span data-ttu-id="ef1a3-150">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="ef1a3-150">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
