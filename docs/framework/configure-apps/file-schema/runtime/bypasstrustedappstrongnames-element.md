---
title: Elemento <bypassTrustedAppStrongNames>
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
ms.openlocfilehash: 96361a6742d1d2f76cb237344189d3277d7c8069
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73739088"
---
# <a name="bypasstrustedappstrongnames-element"></a><span data-ttu-id="23c87-102">Elemento \<bypassTrustedAppStrongNames></span><span class="sxs-lookup"><span data-stu-id="23c87-102">\<bypassTrustedAppStrongNames> Element</span></span>

<span data-ttu-id="23c87-103">Especifica se deve ignorar a validação de nomes fortes em assemblies de confiança total que são carregados em uma confiança total <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="23c87-103">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<bypassTrustedAppStrongNames>**

## <a name="syntax"></a><span data-ttu-id="23c87-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23c87-104">Syntax</span></span>

```xml
<bypassTrustedAppStrongNames
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="23c87-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="23c87-105">Attributes and Elements</span></span>

<span data-ttu-id="23c87-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="23c87-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="23c87-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="23c87-107">Attributes</span></span>

|<span data-ttu-id="23c87-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="23c87-108">Attribute</span></span>|<span data-ttu-id="23c87-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="23c87-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="23c87-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="23c87-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="23c87-111">Especifica se o recurso de bypass que evita a validação de nomes fortes para assemblies de confiança total está habilitado.</span><span class="sxs-lookup"><span data-stu-id="23c87-111">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="23c87-112">Quando esse recurso é habilitado, nomes fortes não são validados quanto à exatidão quando o assembly é carregado.</span><span class="sxs-lookup"><span data-stu-id="23c87-112">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="23c87-113">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="23c87-113">The default is `true`.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="23c87-114">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="23c87-114">enabled Attribute</span></span>

|<span data-ttu-id="23c87-115">Valor</span><span class="sxs-lookup"><span data-stu-id="23c87-115">Value</span></span>|<span data-ttu-id="23c87-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="23c87-116">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="23c87-117">As assinaturas de nome forte em assemblies de confiança total não são validadas quando os assemblies são carregados em uma confiança total <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="23c87-117">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="23c87-118">Este é o padrão.</span><span class="sxs-lookup"><span data-stu-id="23c87-118">This is the default.</span></span>|
|`false`|<span data-ttu-id="23c87-119">As assinaturas de nome forte em assemblies de confiança total são validadas quando os assemblies são carregados em uma confiança total <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="23c87-119">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="23c87-120">A assinatura de nome forte é verificada apenas quanto à exatidão da assinatura; Ela não é comparada com outro nome forte para uma correspondência.</span><span class="sxs-lookup"><span data-stu-id="23c87-120">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="23c87-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="23c87-121">Child Elements</span></span>

<span data-ttu-id="23c87-122">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="23c87-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="23c87-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="23c87-123">Parent Elements</span></span>

|<span data-ttu-id="23c87-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="23c87-124">Element</span></span>|<span data-ttu-id="23c87-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="23c87-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="23c87-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="23c87-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="23c87-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="23c87-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="23c87-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="23c87-128">Remarks</span></span>

<span data-ttu-id="23c87-129">O recurso de bypass de nome forte evita a sobrecarga de verificação de assinatura de nome forte de assemblies de confiança total.</span><span class="sxs-lookup"><span data-stu-id="23c87-129">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>

<span data-ttu-id="23c87-130">O recurso de desvio se aplica a qualquer assembly que está assinado com um nome forte e que tem as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="23c87-130">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>

- <span data-ttu-id="23c87-131">Totalmente confiável sem a <xref:System.Security.Policy.StrongName> evidência (por exemplo, tem `MyComputer` evidências de zona).</span><span class="sxs-lookup"><span data-stu-id="23c87-131">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>

- <span data-ttu-id="23c87-132">Carregado em um <xref:System.AppDomain> totalmente confiável.</span><span class="sxs-lookup"><span data-stu-id="23c87-132">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>

- <span data-ttu-id="23c87-133">Carregado de um local sob a propriedade <xref:System.AppDomainSetup.ApplicationBase%2A> desse <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="23c87-133">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>

- <span data-ttu-id="23c87-134">Não assinado com atraso.</span><span class="sxs-lookup"><span data-stu-id="23c87-134">Not delay-signed.</span></span>

> [!NOTE]
> <span data-ttu-id="23c87-135">Se o recurso de bypass tiver sido desativado para todos os aplicativos no computador usando uma chave do registro, essa configuração do arquivo de configuração não terá nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="23c87-135">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="23c87-136">Para obter mais informações, consulte [como: desabilitar o recurso de bypass de nome forte](../../../../standard/assembly/disable-strong-name-bypass-feature.md).</span><span class="sxs-lookup"><span data-stu-id="23c87-136">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../../standard/assembly/disable-strong-name-bypass-feature.md).</span></span>

## <a name="example"></a><span data-ttu-id="23c87-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="23c87-137">Example</span></span>

<span data-ttu-id="23c87-138">O exemplo a seguir mostra como especificar o comportamento que valida a assinatura de nome forte em assemblies de confiança total.</span><span class="sxs-lookup"><span data-stu-id="23c87-138">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>

```xml
<configuration>
   <runtime>
      <bypassTrustedAppStrongNames enabled="false"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="23c87-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="23c87-139">See also</span></span>

- [<span data-ttu-id="23c87-140">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="23c87-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="23c87-141">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="23c87-141">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="23c87-142">Como desabilitar o recurso de bypass de nome forte</span><span class="sxs-lookup"><span data-stu-id="23c87-142">How to: Disable the strong-name bypass feature</span></span>](../../../../standard/assembly/disable-strong-name-bypass-feature.md)
