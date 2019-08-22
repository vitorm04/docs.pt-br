---
title: Elemento <idn> (Configurações de URI)
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: 5fe2eafee702be96bfdca80a06af4a040d9ef0f6
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664130"
---
# <a name="idn-element-uri-settings"></a><span data-ttu-id="a4e15-102">\<Elemento > IDN (configurações de URI)</span><span class="sxs-lookup"><span data-stu-id="a4e15-102">\<idn> Element (Uri Settings)</span></span>
<span data-ttu-id="a4e15-103">Especifica se a análise de IDN (nome de domínio internacionalizado) é aplicada a um nome de domínio.</span><span class="sxs-lookup"><span data-stu-id="a4e15-103">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="a4e15-104">Hierarquia de esquema</span><span class="sxs-lookup"><span data-stu-id="a4e15-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="a4e15-105">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="a4e15-105">\<configuration> Element</span></span>](../configuration-element.md)  
  
 [<span data-ttu-id="a4e15-106">\<Elemento de > URI (configurações de URI)</span><span class="sxs-lookup"><span data-stu-id="a4e15-106">\<Uri> Element (Uri Settings)</span></span>](uri-element-uri-settings.md)  
  
 [<span data-ttu-id="a4e15-107">\<idn></span><span class="sxs-lookup"><span data-stu-id="a4e15-107">\<idn></span></span>](idn-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="a4e15-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a4e15-108">Syntax</span></span>  
  
```xml  
<idn  
  enabled="All|AllExceptIntranet|None"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4e15-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a4e15-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a4e15-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a4e15-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4e15-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="a4e15-111">Attributes</span></span>  
  
|<span data-ttu-id="a4e15-112">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="a4e15-112">**Element**</span></span>|<span data-ttu-id="a4e15-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="a4e15-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="a4e15-114">Especifica se a análise de IDN (nome de domínio internacionalizado) é aplicada a um nome de domínio, o valor padrão é nenhum.</span><span class="sxs-lookup"><span data-stu-id="a4e15-114">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name The default value is none.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4e15-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a4e15-115">Child Elements</span></span>  
 <span data-ttu-id="a4e15-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a4e15-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a4e15-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a4e15-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a4e15-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="a4e15-118">**Element**</span></span>|<span data-ttu-id="a4e15-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="a4e15-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a4e15-120">uri</span><span class="sxs-lookup"><span data-stu-id="a4e15-120">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="a4e15-121">Contém configurações que especificam como o .NET Framework trata os endereços da Web expressos usando URIs (identificadores de recursos uniformes).</span><span class="sxs-lookup"><span data-stu-id="a4e15-121">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4e15-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="a4e15-122">Remarks</span></span>  
 <span data-ttu-id="a4e15-123">A classe <xref:System.Uri> existente foi estendida no .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="a4e15-123">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="a4e15-124">3,0 SP1 e 2,0 SP1 com suporte para IRI (identificadores de recursos internacionais) e IDNs (nomes de domínio internacionalizados).</span><span class="sxs-lookup"><span data-stu-id="a4e15-124">3.0 SP1, and 2.0 SP1 with support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="a4e15-125">Os usuários atuais não verão nenhuma alteração do comportamento .NET Framework 2,0, a menos que eles especificamente habilitem o suporte a IRI e IDN.</span><span class="sxs-lookup"><span data-stu-id="a4e15-125">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="a4e15-126">Isso garante a compatibilidade do aplicativo com versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a4e15-126">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="a4e15-127">Para habilitar o suporte para IRI, as duas alterações a seguir são necessárias:</span><span class="sxs-lookup"><span data-stu-id="a4e15-127">To enable support for IRI, the following two changes are required:</span></span>  
  
1. <span data-ttu-id="a4e15-128">Adicione a seguinte linha ao arquivo Machine. config no diretório .NET Framework 2,0</span><span class="sxs-lookup"><span data-stu-id="a4e15-128">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="a4e15-129">Especifique se você deseja a análise de nome de domínio internacionalizado (IDN) aplicada ao nome de domínio e se as regras de análise de IRI devem ser aplicadas.</span><span class="sxs-lookup"><span data-stu-id="a4e15-129">Specify whether you want Internationalized Domain Name (IDN) parsing applied to the domain name and whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="a4e15-130">Isso pode ser feito no arquivo machine.config ou em app.config.</span><span class="sxs-lookup"><span data-stu-id="a4e15-130">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="a4e15-131">Há três valores possíveis para IDN, dependendo dos servidores DNS que são usados:</span><span class="sxs-lookup"><span data-stu-id="a4e15-131">There are three possible values for IDN depending on the DNS servers that are used:</span></span>  
  
- <span data-ttu-id="a4e15-132">IDN habilitado = todos</span><span class="sxs-lookup"><span data-stu-id="a4e15-132">idn enabled = All</span></span>  
  
     <span data-ttu-id="a4e15-133">Esse valor converterá todos os nomes de domínio Unicode em seus equivalentes do Punycode (nomes IDN).</span><span class="sxs-lookup"><span data-stu-id="a4e15-133">This value will convert any Unicode domain names to their Punycode equivalents (IDN names).</span></span>  
  
- <span data-ttu-id="a4e15-134">IDN habilitado = AllExceptIntranet</span><span class="sxs-lookup"><span data-stu-id="a4e15-134">idn enabled = AllExceptIntranet</span></span>  
  
     <span data-ttu-id="a4e15-135">Esse valor converterá todos os nomes de domínio Unicode que não estão na intranet local para usar os equivalentes Punycode (nomes IDN).</span><span class="sxs-lookup"><span data-stu-id="a4e15-135">This value will convert all Unicode domain names not on the local Intranet to use the Punycode equivalents (IDN names).</span></span> <span data-ttu-id="a4e15-136">Nesse caso, para lidar com nomes internacionais na intranet local, os servidores DNS que são usados para a intranet devem dar suporte à resolução de nomes Unicode.</span><span class="sxs-lookup"><span data-stu-id="a4e15-136">In this case to handle international names on the local Intranet, the DNS servers that are used for the Intranet should support Unicode name resolution.</span></span>  
  
- <span data-ttu-id="a4e15-137">IDN habilitado = nenhum</span><span class="sxs-lookup"><span data-stu-id="a4e15-137">idn enabled = None</span></span>  
  
     <span data-ttu-id="a4e15-138">Esse valor não converterá nenhum nome de domínio Unicode para usar o Punycode.</span><span class="sxs-lookup"><span data-stu-id="a4e15-138">This value will not convert any Unicode domain names to use Punycode.</span></span> <span data-ttu-id="a4e15-139">Esse é o valor padrão que é consistente com o comportamento .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="a4e15-139">This is the default value which is consistent with the .NET Framework 2.0 behaviour.</span></span>  
  
 <span data-ttu-id="a4e15-140">Habilitar o IDN converterá todos os rótulos Unicode de um nome de domínio para seus equivalentes em Punycode.</span><span class="sxs-lookup"><span data-stu-id="a4e15-140">Enabling IDN will convert all Unicode labels in a domain name to their Punycode equivalents.</span></span> <span data-ttu-id="a4e15-141">Os nomes Punycode contêm apenas caracteres ASCII e sempre começam com o prefixo xn--.</span><span class="sxs-lookup"><span data-stu-id="a4e15-141">Punycode names contain only ASCII characters and always start with the xn-- prefix.</span></span> <span data-ttu-id="a4e15-142">A razão para isso é dar suporte a servidores DNS existentes na Internet, pois a maioria dos servidores DNS dá suporte somente a caracteres ASCII (consulte RFC 3940).</span><span class="sxs-lookup"><span data-stu-id="a4e15-142">The reason for this is to support existing DNS servers on the Internet, since most DNS servers only support ASCII characters (see RFC 3940).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="a4e15-143">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="a4e15-143">Configuration Files</span></span>  
 <span data-ttu-id="a4e15-144">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="a4e15-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4e15-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a4e15-145">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="a4e15-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="a4e15-146">Description</span></span>  
 <span data-ttu-id="a4e15-147">O exemplo a seguir mostra uma configuração usada pela <xref:System.Uri> classe para dar suporte a análise de IRI e nomes IDN.</span><span class="sxs-lookup"><span data-stu-id="a4e15-147">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a4e15-148">Código</span><span class="sxs-lookup"><span data-stu-id="a4e15-148">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4e15-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4e15-149">See also</span></span>

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="a4e15-150">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="a4e15-150">Network Settings Schema</span></span>](index.md)
