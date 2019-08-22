---
title: < elemento de > Crst_DisableSpinWait
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a52dd671f1fbf6fda5bdc92c0935784181eb4b03
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663835"
---
# <a name="crst_disablespinwait-element"></a><span data-ttu-id="882fe-102">\<Elemento de > Crst_DisableSpinWait</span><span class="sxs-lookup"><span data-stu-id="882fe-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="882fe-103">Especifica se é para desabilitar a espera de rotação para uma seção crítica quando contendeda.</span><span class="sxs-lookup"><span data-stu-id="882fe-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span>  
  
 <span data-ttu-id="882fe-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="882fe-104">\<configuration></span></span>  
<span data-ttu-id="882fe-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="882fe-105">\<runtime></span></span>  
<span data-ttu-id="882fe-106">\<> Crst_DisableSpinWait</span><span class="sxs-lookup"><span data-stu-id="882fe-106">\<Crst_DisableSpinWait></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="882fe-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="882fe-107">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="882fe-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="882fe-108">Attributes and Elements</span></span>

<span data-ttu-id="882fe-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="882fe-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="882fe-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="882fe-110">Attributes</span></span>  
  
|<span data-ttu-id="882fe-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="882fe-111">Attribute</span></span>|<span data-ttu-id="882fe-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="882fe-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="882fe-113">**habilitado**</span><span class="sxs-lookup"><span data-stu-id="882fe-113">**enabled**</span></span>|<span data-ttu-id="882fe-114">Especifica se a rotação-aguardando seções críticas quando elas são contendedas está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="882fe-114">Specifies whether spin-waiting for critical sections when they are contended is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="882fe-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="882fe-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="882fe-116">Valor</span><span class="sxs-lookup"><span data-stu-id="882fe-116">Value</span></span>|<span data-ttu-id="882fe-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="882fe-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="882fe-118">1</span><span class="sxs-lookup"><span data-stu-id="882fe-118">1</span></span>|<span data-ttu-id="882fe-119">Desabilitar giro-aguardando quando uma seção crítica não puder ser adquirida.</span><span class="sxs-lookup"><span data-stu-id="882fe-119">Disable spin-waiting when a critical section cannot be acquired.</span></span>|  
|<span data-ttu-id="882fe-120">0</span><span class="sxs-lookup"><span data-stu-id="882fe-120">0</span></span>|<span data-ttu-id="882fe-121">Não desabilite o giro-aguardando quando uma seção crítica não puder ser adquirida.</span><span class="sxs-lookup"><span data-stu-id="882fe-121">Do not disable spin-waiting when a critical section cannot be acquired.</span></span> <span data-ttu-id="882fe-122">Este é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="882fe-122">This is the default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="882fe-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="882fe-123">Child Elements</span></span>  
 <span data-ttu-id="882fe-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="882fe-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="882fe-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="882fe-125">Parent Elements</span></span>  
  
|<span data-ttu-id="882fe-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="882fe-126">Element</span></span>|<span data-ttu-id="882fe-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="882fe-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="882fe-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="882fe-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="882fe-129">Contém informações sobre várias definições de configuração de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="882fe-129">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="882fe-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="882fe-130">Example</span></span>  

<span data-ttu-id="882fe-131">O exemplo a seguir desabilita a espera de rotação em seções críticas quando contendeda.</span><span class="sxs-lookup"><span data-stu-id="882fe-131">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="882fe-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="882fe-132">See also</span></span>

- [<span data-ttu-id="882fe-133">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="882fe-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="882fe-134">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="882fe-134">Configuration File Schema</span></span>](../index.md)
