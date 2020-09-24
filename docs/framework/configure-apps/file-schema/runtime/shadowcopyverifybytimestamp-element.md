---
title: Elemento <shadowCopyVerifyByTimestamp>
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
ms.openlocfilehash: c0dc190e69ca9650d518ee297b12f79f8c47d58b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183969"
---
# <a name="shadowcopyverifybytimestamp-element"></a><span data-ttu-id="706b6-102">Elemento \<shadowCopyVerifyByTimestamp></span><span class="sxs-lookup"><span data-stu-id="706b6-102">\<shadowCopyVerifyByTimestamp> Element</span></span>

<span data-ttu-id="706b6-103">Especifica se a cópia de sombra usa o comportamento de inicialização padrão introduzido no .NET Framework 4 ou reverte para o comportamento de inicialização de versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="706b6-103">Specifies whether shadow copying uses the default startup behavior introduced in the .NET Framework 4, or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<shadowCopyVerifyByTimestamp>**  
  
## <a name="syntax"></a><span data-ttu-id="706b6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="706b6-104">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="706b6-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="706b6-105">Attributes and Elements</span></span>  

 <span data-ttu-id="706b6-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="706b6-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="706b6-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="706b6-107">Attributes</span></span>  
  
|<span data-ttu-id="706b6-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="706b6-108">Attribute</span></span>|<span data-ttu-id="706b6-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="706b6-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="706b6-110">Habilitado</span><span class="sxs-lookup"><span data-stu-id="706b6-110">enabled</span></span>|<span data-ttu-id="706b6-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="706b6-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="706b6-112">Especifica se os domínios de aplicativo que usam a cópia de sombra comparam carimbos de data/hora ao iniciar, para determinar se um assembly foi atualizado antes de copiar a sombra do assembly.</span><span class="sxs-lookup"><span data-stu-id="706b6-112">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="706b6-113">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="706b6-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="706b6-114">Valor</span><span class="sxs-lookup"><span data-stu-id="706b6-114">Value</span></span>|<span data-ttu-id="706b6-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="706b6-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="706b6-116">true</span><span class="sxs-lookup"><span data-stu-id="706b6-116">true</span></span>|<span data-ttu-id="706b6-117">Na inicialização, o copia somente os assemblies que foram atualizados desde a última vez que foram copiados para o diretório de cópia de sombra.</span><span class="sxs-lookup"><span data-stu-id="706b6-117">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="706b6-118">Esse é o padrão para o .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="706b6-118">This is the default for the .NET Framework 4.</span></span>|  
|<span data-ttu-id="706b6-119">false</span><span class="sxs-lookup"><span data-stu-id="706b6-119">false</span></span>|<span data-ttu-id="706b6-120">Reverte para o comportamento de inicialização de versões anteriores do .NET Framework, que era copiar todos os arquivos na inicialização.</span><span class="sxs-lookup"><span data-stu-id="706b6-120">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="706b6-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="706b6-121">Child Elements</span></span>  

 <span data-ttu-id="706b6-122">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="706b6-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="706b6-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="706b6-123">Parent Elements</span></span>  
  
|<span data-ttu-id="706b6-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="706b6-124">Element</span></span>|<span data-ttu-id="706b6-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="706b6-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="706b6-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="706b6-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="706b6-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="706b6-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="706b6-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="706b6-128">Remarks</span></span>  

 <span data-ttu-id="706b6-129">A partir do .NET Framework 4, os assemblies serão copiados por sombra somente se os carimbos de data/hora indicarem que foram alterados desde que foram copiados pela última vez para o diretório de cópia de sombra.</span><span class="sxs-lookup"><span data-stu-id="706b6-129">Starting with the .NET Framework 4, assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="706b6-130">Isso melhora os tempos de inicialização para muitos aplicativos que usam cópia de sombra, conforme descrito em [assemblies de cópia de sombra](../../../app-domains/shadow-copy-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="706b6-130">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="706b6-131">Aplicativos que têm uma alta porcentagem e frequência de atualizações de assembly podem não se beneficiar dessa alteração no comportamento.</span><span class="sxs-lookup"><span data-stu-id="706b6-131">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="706b6-132">Nesse caso, você pode usar esse elemento para restaurar o comportamento de versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="706b6-132">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="706b6-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="706b6-133">Example</span></span>  

 <span data-ttu-id="706b6-134">O exemplo a seguir mostra como desabilitar o comportamento de inicialização padrão da cópia de sombra no .NET Framework 4 e reverter para o comportamento de inicialização de versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="706b6-134">The following example shows how to disable the default startup behavior of shadow copying in the .NET Framework 4, and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="706b6-135">Veja também</span><span class="sxs-lookup"><span data-stu-id="706b6-135">See also</span></span>

- [<span data-ttu-id="706b6-136">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="706b6-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="706b6-137">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="706b6-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="706b6-138">Criando cópias de sombra de assemblies</span><span class="sxs-lookup"><span data-stu-id="706b6-138">Shadow Copying Assemblies</span></span>](../../../app-domains/shadow-copy-assemblies.md)
