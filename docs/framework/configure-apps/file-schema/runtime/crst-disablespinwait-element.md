---
title: elemento < Crst_DisableSpinWait >
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f89f0558c11e229fef2ca3cd619e3c033f12c858
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754668"
---
# <a name="crstdisablespinwait-element"></a><span data-ttu-id="7eaf2-102">\<Crst_DisableSpinWait > elemento</span><span class="sxs-lookup"><span data-stu-id="7eaf2-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="7eaf2-103">Especifica se é necessário desabilitar rotação-aguardando uma seção crítica quando sustentados.</span><span class="sxs-lookup"><span data-stu-id="7eaf2-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span>  
  
 <span data-ttu-id="7eaf2-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="7eaf2-104">\<configuration></span></span>  
<span data-ttu-id="7eaf2-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="7eaf2-105">\<runtime></span></span>  
<span data-ttu-id="7eaf2-106">\<Crst_DisableSpinWait></span><span class="sxs-lookup"><span data-stu-id="7eaf2-106">\<Crst_DisableSpinWait></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eaf2-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7eaf2-107">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7eaf2-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7eaf2-108">Attributes and Elements</span></span>

<span data-ttu-id="7eaf2-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7eaf2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7eaf2-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="7eaf2-110">Attributes</span></span>  
  
|<span data-ttu-id="7eaf2-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="7eaf2-111">Attribute</span></span>|<span data-ttu-id="7eaf2-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="7eaf2-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7eaf2-113">**enabled**</span><span class="sxs-lookup"><span data-stu-id="7eaf2-113">**enabled**</span></span>|<span data-ttu-id="7eaf2-114">Especifica se a espera de rotação para seções críticas quando eles são sustentados está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="7eaf2-114">Specifies whether spin-waiting for critical sections when they are contended is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="7eaf2-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="7eaf2-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="7eaf2-116">Valor</span><span class="sxs-lookup"><span data-stu-id="7eaf2-116">Value</span></span>|<span data-ttu-id="7eaf2-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="7eaf2-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7eaf2-118">1</span><span class="sxs-lookup"><span data-stu-id="7eaf2-118">1</span></span>|<span data-ttu-id="7eaf2-119">Desabilite espera de rotação quando não é possível adquirir uma seção crítica.</span><span class="sxs-lookup"><span data-stu-id="7eaf2-119">Disable spin-waiting when a critical section cannot be acquired.</span></span>|  
|<span data-ttu-id="7eaf2-120">0</span><span class="sxs-lookup"><span data-stu-id="7eaf2-120">0</span></span>|<span data-ttu-id="7eaf2-121">Não desabilite espera de rotação quando não é possível adquirir uma seção crítica.</span><span class="sxs-lookup"><span data-stu-id="7eaf2-121">Do not disable spin-waiting when a critical section cannot be acquired.</span></span> <span data-ttu-id="7eaf2-122">Este é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="7eaf2-122">This is the default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7eaf2-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7eaf2-123">Child Elements</span></span>  
 <span data-ttu-id="7eaf2-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7eaf2-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7eaf2-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7eaf2-125">Parent Elements</span></span>  
  
|<span data-ttu-id="7eaf2-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="7eaf2-126">Element</span></span>|<span data-ttu-id="7eaf2-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="7eaf2-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7eaf2-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7eaf2-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7eaf2-129">Contém informações sobre várias definições de configuração de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7eaf2-129">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7eaf2-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7eaf2-130">Example</span></span>  

<span data-ttu-id="7eaf2-131">A exemplo a seguir desabilita espera de rotação em seções críticas quando sustentados.</span><span class="sxs-lookup"><span data-stu-id="7eaf2-131">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7eaf2-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7eaf2-132">See also</span></span>

- [<span data-ttu-id="7eaf2-133">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="7eaf2-133">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="7eaf2-134">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="7eaf2-134">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
