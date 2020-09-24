---
title: Elemento <Crst_DisableSpinWait>
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
ms.openlocfilehash: 45052d99bb297ac39d058fa405fe57a7c991f738
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151344"
---
# <a name="crst_disablespinwait-element"></a><span data-ttu-id="00c4f-102">Elemento \<Crst_DisableSpinWait></span><span class="sxs-lookup"><span data-stu-id="00c4f-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="00c4f-103">Especifica se é para desabilitar a espera de rotação para uma seção crítica quando contendeda.</span><span class="sxs-lookup"><span data-stu-id="00c4f-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Crst_DisableSpinWait>**  
  
## <a name="syntax"></a><span data-ttu-id="00c4f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="00c4f-104">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00c4f-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="00c4f-105">Attributes and Elements</span></span>

<span data-ttu-id="00c4f-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="00c4f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00c4f-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="00c4f-107">Attributes</span></span>  
  
|<span data-ttu-id="00c4f-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="00c4f-108">Attribute</span></span>|<span data-ttu-id="00c4f-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="00c4f-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="00c4f-110">**habilitado**</span><span class="sxs-lookup"><span data-stu-id="00c4f-110">**enabled**</span></span>|<span data-ttu-id="00c4f-111">Especifica se a rotação-aguardando seções críticas quando elas são contendedas está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="00c4f-111">Specifies whether spin-waiting for critical sections when they are contended is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="00c4f-112">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="00c4f-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="00c4f-113">Valor</span><span class="sxs-lookup"><span data-stu-id="00c4f-113">Value</span></span>|<span data-ttu-id="00c4f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="00c4f-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="00c4f-115">1</span><span class="sxs-lookup"><span data-stu-id="00c4f-115">1</span></span>|<span data-ttu-id="00c4f-116">Desabilitar giro-aguardando quando uma seção crítica não puder ser adquirida.</span><span class="sxs-lookup"><span data-stu-id="00c4f-116">Disable spin-waiting when a critical section cannot be acquired.</span></span>|  
|<span data-ttu-id="00c4f-117">0</span><span class="sxs-lookup"><span data-stu-id="00c4f-117">0</span></span>|<span data-ttu-id="00c4f-118">Não desabilite o giro-aguardando quando uma seção crítica não puder ser adquirida.</span><span class="sxs-lookup"><span data-stu-id="00c4f-118">Do not disable spin-waiting when a critical section cannot be acquired.</span></span> <span data-ttu-id="00c4f-119">Esse é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="00c4f-119">This is the default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="00c4f-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="00c4f-120">Child Elements</span></span>  

 <span data-ttu-id="00c4f-121">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="00c4f-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="00c4f-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="00c4f-122">Parent Elements</span></span>  
  
|<span data-ttu-id="00c4f-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="00c4f-123">Element</span></span>|<span data-ttu-id="00c4f-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="00c4f-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="00c4f-125">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="00c4f-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="00c4f-126">Contém informações sobre várias definições de configuração de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="00c4f-126">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="00c4f-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="00c4f-127">Example</span></span>  

<span data-ttu-id="00c4f-128">O exemplo a seguir desabilita a espera de rotação em seções críticas quando contendeda.</span><span class="sxs-lookup"><span data-stu-id="00c4f-128">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="00c4f-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="00c4f-129">See also</span></span>

- [<span data-ttu-id="00c4f-130">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="00c4f-130">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="00c4f-131">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="00c4f-131">Configuration File Schema</span></span>](../index.md)
