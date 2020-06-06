---
title: Elemento <gcAllowVeryLargeObjects>
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: 8b2f39a0867228474afdee788474fda11f14ca82
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154121"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="45395-102">Elemento \<gcAllowVeryLargeObjects></span><span class="sxs-lookup"><span data-stu-id="45395-102">\<gcAllowVeryLargeObjects> Element</span></span>
<span data-ttu-id="45395-103">Em plataformas de 64 bits, habilita matrizes com mais de 2 gigabytes (GB) de tamanho total.</span><span class="sxs-lookup"><span data-stu-id="45395-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**  
  
## <a name="syntax"></a><span data-ttu-id="45395-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="45395-104">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45395-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="45395-105">Attributes and Elements</span></span>  
 <span data-ttu-id="45395-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="45395-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45395-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="45395-107">Attributes</span></span>  
  
|<span data-ttu-id="45395-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="45395-108">Attribute</span></span>|<span data-ttu-id="45395-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="45395-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="45395-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="45395-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="45395-111">Especifica se as matrizes maiores que 2 GB no tamanho total estão habilitadas em plataformas de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="45395-111">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="45395-112">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="45395-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="45395-113">Valor</span><span class="sxs-lookup"><span data-stu-id="45395-113">Value</span></span>|<span data-ttu-id="45395-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="45395-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="45395-115">Matrizes maiores que 2 GB no tamanho total não estão habilitadas.</span><span class="sxs-lookup"><span data-stu-id="45395-115">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="45395-116">Este é o padrão.</span><span class="sxs-lookup"><span data-stu-id="45395-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="45395-117">Matrizes maiores que 2 GB no tamanho total são habilitadas em plataformas de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="45395-117">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="45395-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="45395-118">Child Elements</span></span>  
 <span data-ttu-id="45395-119">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="45395-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="45395-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="45395-120">Parent Elements</span></span>  
  
|<span data-ttu-id="45395-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="45395-121">Element</span></span>|<span data-ttu-id="45395-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="45395-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="45395-123">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="45395-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="45395-124">Contém informações sobre opções de inicialização do runtime.</span><span class="sxs-lookup"><span data-stu-id="45395-124">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45395-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="45395-125">Remarks</span></span>  
 <span data-ttu-id="45395-126">O uso desse elemento em seu arquivo de configuração de aplicativo permite que matrizes com mais de 2 GB de tamanho, mas não alteram outros limites no tamanho do objeto ou tamanho da matriz:</span><span class="sxs-lookup"><span data-stu-id="45395-126">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="45395-127">O número máximo de elementos em uma matriz é <xref:System.UInt32.MaxValue?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="45395-127">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="45395-128">O índice máximo em qualquer dimensão única é 2.147.483.591 (0x7FFFFFC7) para matrizes de bytes e matrizes de estruturas de byte único e 2.146.435.071 (0X7FEFFFFF) para outros tipos.</span><span class="sxs-lookup"><span data-stu-id="45395-128">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
- <span data-ttu-id="45395-129">O tamanho máximo para cadeias de caracteres e outros objetos que não são da matriz não são alterados.</span><span class="sxs-lookup"><span data-stu-id="45395-129">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="45395-130">Antes de habilitar esse recurso, verifique se o seu aplicativo não inclui um código não seguro que assuma que todas as matrizes tenham menos de 2 GB de tamanho.</span><span class="sxs-lookup"><span data-stu-id="45395-130">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="45395-131">Por exemplo, o código não seguro que usa matrizes como buffers pode ser suscetível a estouros de buffer se ele for escrito na suposição de que as matrizes não excederão 2 GB.</span><span class="sxs-lookup"><span data-stu-id="45395-131">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45395-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="45395-132">Example</span></span>  
 <span data-ttu-id="45395-133">O exemplo a seguir mostra como habilitar esse recurso para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="45395-133">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="45395-134">Com suporte em</span><span class="sxs-lookup"><span data-stu-id="45395-134">Supported in</span></span>

<span data-ttu-id="45395-135">.NET Framework 4,5 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="45395-135">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="45395-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="45395-136">See also</span></span>

- [<span data-ttu-id="45395-137">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="45395-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="45395-138">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="45395-138">Configuration File Schema</span></span>](../index.md)
