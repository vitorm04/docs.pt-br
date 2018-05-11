---
title: '&lt;IDN&gt; elemento (configurações de Uri)'
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 17f68fbb92797928be911e530232e8638793687f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltidngt-element-uri-settings"></a><span data-ttu-id="5d0ba-102">&lt;IDN&gt; elemento (configurações de Uri)</span><span class="sxs-lookup"><span data-stu-id="5d0ba-102">&lt;idn&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="5d0ba-103">Especifica se a análise de nome de domínio internacionalizado (IDN) é aplicada a um nome de domínio.</span><span class="sxs-lookup"><span data-stu-id="5d0ba-103">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="5d0ba-104">Hierarquia de esquema</span><span class="sxs-lookup"><span data-stu-id="5d0ba-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="5d0ba-105">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="5d0ba-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="5d0ba-106">\<URI > elemento (configurações de Uri)</span><span class="sxs-lookup"><span data-stu-id="5d0ba-106">\<Uri> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [<span data-ttu-id="5d0ba-107">\<IDN ></span><span class="sxs-lookup"><span data-stu-id="5d0ba-107">\<idn></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="5d0ba-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d0ba-108">Syntax</span></span>  
  
```xml  
<idn  
  enabled="All|AllExceptIntranet|None"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d0ba-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5d0ba-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5d0ba-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5d0ba-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d0ba-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="5d0ba-111">Attributes</span></span>  
  
|<span data-ttu-id="5d0ba-112">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="5d0ba-112">**Element**</span></span>|<span data-ttu-id="5d0ba-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="5d0ba-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="5d0ba-114">Especifica que se a análise de nome de domínio internacionalizado (IDN) é aplicado a um nome de domínio o valor padrão é none.</span><span class="sxs-lookup"><span data-stu-id="5d0ba-114">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name The default value is none.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5d0ba-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5d0ba-115">Child Elements</span></span>  
 <span data-ttu-id="5d0ba-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5d0ba-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5d0ba-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5d0ba-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5d0ba-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="5d0ba-118">**Element**</span></span>|<span data-ttu-id="5d0ba-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="5d0ba-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5d0ba-120">URI</span><span class="sxs-lookup"><span data-stu-id="5d0ba-120">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="5d0ba-121">Contém configurações que especificam como o .NET Framework controla endereços da web expressados usando identificadores de recurso uniformes (URIs).</span><span class="sxs-lookup"><span data-stu-id="5d0ba-121">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d0ba-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="5d0ba-122">Remarks</span></span>  
 <span data-ttu-id="5d0ba-123">Existente <xref:System.Uri> classe foi estendida no .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="5d0ba-123">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="5d0ba-124">3.0 SP1 e 2.0 SP1 com suporte para identificadores de recursos internacionais (IRI) e nomes de domínio internacionalizados (IDNS).</span><span class="sxs-lookup"><span data-stu-id="5d0ba-124">3.0 SP1, and 2.0 SP1 with support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="5d0ba-125">Os usuários atuais não verão qualquer alteração no comportamento do .NET Framework 2.0, a menos que eles permitem especificamente IRI e IDN suporte.</span><span class="sxs-lookup"><span data-stu-id="5d0ba-125">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="5d0ba-126">Isso garante a compatibilidade do aplicativo com versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5d0ba-126">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="5d0ba-127">Para habilitar o suporte para IRI, as alterações a seguir são necessárias:</span><span class="sxs-lookup"><span data-stu-id="5d0ba-127">To enable support for IRI, the following two changes are required:</span></span>  
  
1.  <span data-ttu-id="5d0ba-128">Adicione a seguinte linha no arquivo Machine. config no diretório do .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="5d0ba-128">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  <span data-ttu-id="5d0ba-129">Especifique se deseja que a análise de nome de domínio internacionalizado (IDN) aplicado ao nome de domínio e se as regras de análise de IRI deve ser aplicada.</span><span class="sxs-lookup"><span data-stu-id="5d0ba-129">Specify whether you want Internationalized Domain Name (IDN) parsing applied to the domain name and whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="5d0ba-130">Isso pode ser feito no arquivo machine.config ou em app.config.</span><span class="sxs-lookup"><span data-stu-id="5d0ba-130">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="5d0ba-131">Há três valores possíveis para IDN dependendo os servidores DNS que são usados:</span><span class="sxs-lookup"><span data-stu-id="5d0ba-131">There are three possible values for IDN depending on the DNS servers that are used:</span></span>  
  
-   <span data-ttu-id="5d0ba-132">IDN habilitado = All</span><span class="sxs-lookup"><span data-stu-id="5d0ba-132">idn enabled = All</span></span>  
  
     <span data-ttu-id="5d0ba-133">Esse valor converterá todos os nomes de domínio Unicode em seus equivalentes do Punycode (nomes IDN).</span><span class="sxs-lookup"><span data-stu-id="5d0ba-133">This value will convert any Unicode domain names to their Punycode equivalents (IDN names).</span></span>  
  
-   <span data-ttu-id="5d0ba-134">IDN habilitado = AllExceptIntranet</span><span class="sxs-lookup"><span data-stu-id="5d0ba-134">idn enabled = AllExceptIntranet</span></span>  
  
     <span data-ttu-id="5d0ba-135">Esse valor serão convertidos em todos os nomes de domínio de Unicode não na Intranet local para usar os equivalentes de Punycode (nomes IDN).</span><span class="sxs-lookup"><span data-stu-id="5d0ba-135">This value will convert all Unicode domain names not on the local Intranet to use the Punycode equivalents (IDN names).</span></span> <span data-ttu-id="5d0ba-136">Nesse caso para lidar com nomes internacionais da intranet local, os servidores DNS que são usados para a Intranet devem dar suporte a resolução de nomes de Unicode.</span><span class="sxs-lookup"><span data-stu-id="5d0ba-136">In this case to handle international names on the local Intranet, the DNS servers that are used for the Intranet should support Unicode name resolution.</span></span>  
  
-   <span data-ttu-id="5d0ba-137">IDN habilitado = nenhum</span><span class="sxs-lookup"><span data-stu-id="5d0ba-137">idn enabled = None</span></span>  
  
     <span data-ttu-id="5d0ba-138">Esse valor não converterá nenhum nome de domínio Unicode para usar o Punycode.</span><span class="sxs-lookup"><span data-stu-id="5d0ba-138">This value will not convert any Unicode domain names to use Punycode.</span></span> <span data-ttu-id="5d0ba-139">Este é o valor padrão que é consistente com o comportamento do .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="5d0ba-139">This is the default value which is consistent with the .NET Framework 2.0 behaviour.</span></span>  
  
 <span data-ttu-id="5d0ba-140">Habilitar o IDN converterá todos os rótulos Unicode de um nome de domínio para seus equivalentes em Punycode.</span><span class="sxs-lookup"><span data-stu-id="5d0ba-140">Enabling IDN will convert all Unicode labels in a domain name to their Punycode equivalents.</span></span> <span data-ttu-id="5d0ba-141">Os nomes Punycode contêm apenas caracteres ASCII e sempre começam com o prefixo xn--.</span><span class="sxs-lookup"><span data-stu-id="5d0ba-141">Punycode names contain only ASCII characters and always start with the xn-- prefix.</span></span> <span data-ttu-id="5d0ba-142">A razão para isso é dar suporte a servidores DNS existentes na Internet, pois a maioria dos servidores DNS dá suporte somente a caracteres ASCII (consulte RFC 3940).</span><span class="sxs-lookup"><span data-stu-id="5d0ba-142">The reason for this is to support existing DNS servers on the Internet, since most DNS servers only support ASCII characters (see RFC 3940).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="5d0ba-143">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="5d0ba-143">Configuration Files</span></span>  
 <span data-ttu-id="5d0ba-144">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="5d0ba-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d0ba-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5d0ba-145">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="5d0ba-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d0ba-146">Description</span></span>  
 <span data-ttu-id="5d0ba-147">O exemplo a seguir mostra uma configuração usada pela <xref:System.Uri> classe para dar suporte a análise de IRI e nomes IDN.</span><span class="sxs-lookup"><span data-stu-id="5d0ba-147">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5d0ba-148">Código</span><span class="sxs-lookup"><span data-stu-id="5d0ba-148">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5d0ba-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d0ba-149">See Also</span></span>  
 <xref:System.Configuration.IdnElement?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 [<span data-ttu-id="5d0ba-150">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="5d0ba-150">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
