---
title: Elemento <bypassTrustedAppStrongNames>
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
ms.openlocfilehash: 50e67e97d74b896a680cc18270d32aa7a8eb8035
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118174"
---
# <a name="bypasstrustedappstrongnames-element"></a><span data-ttu-id="8e1fe-102">\<Elemento bypassTrustedAppStrongNames></span><span class="sxs-lookup"><span data-stu-id="8e1fe-102">\<bypassTrustedAppStrongNames> Element</span></span>

<span data-ttu-id="8e1fe-103">Especifica se deve ignorar a validação de nomes fortes em assemblies de confiança total que são carregados em um <xref:System.AppDomain>de confiança total.</span><span class="sxs-lookup"><span data-stu-id="8e1fe-103">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>

<span data-ttu-id="8e1fe-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8e1fe-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8e1fe-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="8e1fe-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="8e1fe-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<bypassTrustedAppStrongNames >**</span><span class="sxs-lookup"><span data-stu-id="8e1fe-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<bypassTrustedAppStrongNames>**</span></span>

## <a name="syntax"></a><span data-ttu-id="8e1fe-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e1fe-107">Syntax</span></span>

```xml
<bypassTrustedAppStrongNames
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8e1fe-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8e1fe-108">Attributes and Elements</span></span>

<span data-ttu-id="8e1fe-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8e1fe-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8e1fe-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="8e1fe-110">Attributes</span></span>

|<span data-ttu-id="8e1fe-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="8e1fe-111">Attribute</span></span>|<span data-ttu-id="8e1fe-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e1fe-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="8e1fe-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="8e1fe-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="8e1fe-114">Especifica se o recurso de bypass que evita a validação de nomes fortes para assemblies de confiança total está habilitado.</span><span class="sxs-lookup"><span data-stu-id="8e1fe-114">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="8e1fe-115">Quando esse recurso é habilitado, nomes fortes não são validados quanto à exatidão quando o assembly é carregado.</span><span class="sxs-lookup"><span data-stu-id="8e1fe-115">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="8e1fe-116">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="8e1fe-116">The default is `true`.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="8e1fe-117">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="8e1fe-117">enabled Attribute</span></span>

|<span data-ttu-id="8e1fe-118">Valor</span><span class="sxs-lookup"><span data-stu-id="8e1fe-118">Value</span></span>|<span data-ttu-id="8e1fe-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e1fe-119">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="8e1fe-120">As assinaturas de nome forte em assemblies de confiança total não são validadas quando os assemblies são carregados em um <xref:System.AppDomain>de confiança total.</span><span class="sxs-lookup"><span data-stu-id="8e1fe-120">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="8e1fe-121">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="8e1fe-121">This is the default.</span></span>|
|`false`|<span data-ttu-id="8e1fe-122">As assinaturas de nome forte em assemblies de confiança total são validadas quando os assemblies são carregados em um <xref:System.AppDomain>de confiança total.</span><span class="sxs-lookup"><span data-stu-id="8e1fe-122">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="8e1fe-123">A assinatura de nome forte é verificada apenas quanto à exatidão da assinatura; Ela não é comparada com outro nome forte para uma correspondência.</span><span class="sxs-lookup"><span data-stu-id="8e1fe-123">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="8e1fe-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8e1fe-124">Child Elements</span></span>

<span data-ttu-id="8e1fe-125">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8e1fe-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8e1fe-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8e1fe-126">Parent Elements</span></span>

|<span data-ttu-id="8e1fe-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="8e1fe-127">Element</span></span>|<span data-ttu-id="8e1fe-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e1fe-128">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="8e1fe-129">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8e1fe-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="8e1fe-130">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="8e1fe-130">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8e1fe-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="8e1fe-131">Remarks</span></span>

<span data-ttu-id="8e1fe-132">O recurso de bypass de nome forte evita a sobrecarga de verificação de assinatura de nome forte de assemblies de confiança total.</span><span class="sxs-lookup"><span data-stu-id="8e1fe-132">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>

<span data-ttu-id="8e1fe-133">O recurso de desvio se aplica a qualquer assembly que está assinado com um nome forte e que tem as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="8e1fe-133">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>

- <span data-ttu-id="8e1fe-134">Totalmente confiável sem a evidência de <xref:System.Security.Policy.StrongName> (por exemplo, tem evidências de zona de `MyComputer`).</span><span class="sxs-lookup"><span data-stu-id="8e1fe-134">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>

- <span data-ttu-id="8e1fe-135">Carregado em um <xref:System.AppDomain> totalmente confiável.</span><span class="sxs-lookup"><span data-stu-id="8e1fe-135">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>

- <span data-ttu-id="8e1fe-136">Carregado de um local sob a propriedade <xref:System.AppDomainSetup.ApplicationBase%2A> desse <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="8e1fe-136">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>

- <span data-ttu-id="8e1fe-137">Não assinado com atraso.</span><span class="sxs-lookup"><span data-stu-id="8e1fe-137">Not delay-signed.</span></span>

> [!NOTE]
> <span data-ttu-id="8e1fe-138">Se o recurso de bypass tiver sido desativado para todos os aplicativos no computador usando uma chave do registro, essa configuração do arquivo de configuração não terá nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="8e1fe-138">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="8e1fe-139">Para obter mais informações, consulte [como: desabilitar o recurso de bypass de nome forte](../../../app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span><span class="sxs-lookup"><span data-stu-id="8e1fe-139">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span></span>

## <a name="example"></a><span data-ttu-id="8e1fe-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8e1fe-140">Example</span></span>

<span data-ttu-id="8e1fe-141">O exemplo a seguir mostra como especificar o comportamento que valida a assinatura de nome forte em assemblies de confiança total.</span><span class="sxs-lookup"><span data-stu-id="8e1fe-141">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>

```xml
<configuration>
   <runtime>
      <bypassTrustedAppStrongNames enabled="false"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="8e1fe-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e1fe-142">See also</span></span>

- [<span data-ttu-id="8e1fe-143">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="8e1fe-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="8e1fe-144">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="8e1fe-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="8e1fe-145">Como desabilitar o recurso de bypass de nome forte</span><span class="sxs-lookup"><span data-stu-id="8e1fe-145">How to: Disable the strong-name bypass feature</span></span>](../../../../standard/assembly/disable-strong-name-bypass-feature.md)
