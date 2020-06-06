---
title: Elemento <shadowCopyVerifyByTimestamp>
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
ms.openlocfilehash: 160f14c856735e1ceac8635506aea52454faea43
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115735"
---
# <a name="shadowcopyverifybytimestamp-element"></a><span data-ttu-id="836c3-102">Elemento \<shadowCopyVerifyByTimestamp></span><span class="sxs-lookup"><span data-stu-id="836c3-102">\<shadowCopyVerifyByTimestamp> Element</span></span>
<span data-ttu-id="836c3-103">Especifica se a cópia de sombra usa o comportamento de inicialização padrão introduzido no .NET Framework 4 ou reverte para o comportamento de inicialização de versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="836c3-103">Specifies whether shadow copying uses the default startup behavior introduced in the .NET Framework 4, or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<shadowCopyVerifyByTimestamp>**  
  
## <a name="syntax"></a><span data-ttu-id="836c3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="836c3-104">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="836c3-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="836c3-105">Attributes and Elements</span></span>  
 <span data-ttu-id="836c3-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="836c3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="836c3-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="836c3-107">Attributes</span></span>  
  
|<span data-ttu-id="836c3-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="836c3-108">Attribute</span></span>|<span data-ttu-id="836c3-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="836c3-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="836c3-110">Habilitado</span><span class="sxs-lookup"><span data-stu-id="836c3-110">enabled</span></span>|<span data-ttu-id="836c3-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="836c3-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="836c3-112">Especifica se os domínios de aplicativo que usam a cópia de sombra comparam carimbos de data/hora ao iniciar, para determinar se um assembly foi atualizado antes de copiar a sombra do assembly.</span><span class="sxs-lookup"><span data-stu-id="836c3-112">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="836c3-113">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="836c3-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="836c3-114">Valor</span><span class="sxs-lookup"><span data-stu-id="836c3-114">Value</span></span>|<span data-ttu-id="836c3-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="836c3-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="836c3-116">true</span><span class="sxs-lookup"><span data-stu-id="836c3-116">true</span></span>|<span data-ttu-id="836c3-117">Na inicialização, o copia somente os assemblies que foram atualizados desde a última vez que foram copiados para o diretório de cópia de sombra.</span><span class="sxs-lookup"><span data-stu-id="836c3-117">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="836c3-118">Esse é o padrão para o .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="836c3-118">This is the default for the .NET Framework 4.</span></span>|  
|<span data-ttu-id="836c3-119">false</span><span class="sxs-lookup"><span data-stu-id="836c3-119">false</span></span>|<span data-ttu-id="836c3-120">Reverte para o comportamento de inicialização de versões anteriores do .NET Framework, que era copiar todos os arquivos na inicialização.</span><span class="sxs-lookup"><span data-stu-id="836c3-120">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="836c3-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="836c3-121">Child Elements</span></span>  
 <span data-ttu-id="836c3-122">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="836c3-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="836c3-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="836c3-123">Parent Elements</span></span>  
  
|<span data-ttu-id="836c3-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="836c3-124">Element</span></span>|<span data-ttu-id="836c3-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="836c3-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="836c3-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="836c3-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="836c3-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="836c3-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="836c3-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="836c3-128">Remarks</span></span>  
 <span data-ttu-id="836c3-129">A partir do .NET Framework 4, os assemblies serão copiados por sombra somente se os carimbos de data/hora indicarem que foram alterados desde que foram copiados pela última vez para o diretório de cópia de sombra.</span><span class="sxs-lookup"><span data-stu-id="836c3-129">Starting with the .NET Framework 4, assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="836c3-130">Isso melhora os tempos de inicialização para muitos aplicativos que usam cópia de sombra, conforme descrito em [assemblies de cópia de sombra](../../../app-domains/shadow-copy-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="836c3-130">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="836c3-131">Aplicativos que têm uma alta porcentagem e frequência de atualizações de assembly podem não se beneficiar dessa alteração no comportamento.</span><span class="sxs-lookup"><span data-stu-id="836c3-131">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="836c3-132">Nesse caso, você pode usar esse elemento para restaurar o comportamento de versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="836c3-132">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="836c3-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="836c3-133">Example</span></span>  
 <span data-ttu-id="836c3-134">O exemplo a seguir mostra como desabilitar o comportamento de inicialização padrão da cópia de sombra no .NET Framework 4 e reverter para o comportamento de inicialização de versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="836c3-134">The following example shows how to disable the default startup behavior of shadow copying in the .NET Framework 4, and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="836c3-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="836c3-135">See also</span></span>

- [<span data-ttu-id="836c3-136">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="836c3-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="836c3-137">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="836c3-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="836c3-138">Criando cópias de sombra de assemblies</span><span class="sxs-lookup"><span data-stu-id="836c3-138">Shadow Copying Assemblies</span></span>](../../../app-domains/shadow-copy-assemblies.md)
