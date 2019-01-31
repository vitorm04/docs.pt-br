---
title: Elemento <UseRandomizedStringHashAlgorithm>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UseRandomizedStringHashAlgorithm element
- <UseRandomizedStringHashAlgorithm> element
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3545938d8f9a59c8f3c6d03e5e67bb5f545a4981
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260587"
---
# <a name="userandomizedstringhashalgorithm-element"></a><span data-ttu-id="d046f-102">\<UseRandomizedStringHashAlgorithm > elemento</span><span class="sxs-lookup"><span data-stu-id="d046f-102">\<UseRandomizedStringHashAlgorithm> Element</span></span>
<span data-ttu-id="d046f-103">Determina se o common language runtime calcula códigos hash para cadeias de caracteres em uma base de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d046f-103">Determines whether the common language runtime calculates hash codes for strings on a per application domain basis.</span></span>  
  
 <span data-ttu-id="d046f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d046f-104">\<configuration></span></span>  
<span data-ttu-id="d046f-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="d046f-105">\<runtime></span></span>  
<span data-ttu-id="d046f-106">\<UseRandomizedStringHashAlgorithm></span><span class="sxs-lookup"><span data-stu-id="d046f-106">\<UseRandomizedStringHashAlgorithm></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d046f-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d046f-107">Syntax</span></span>  
  
```xml  
<UseRandomizedStringHashAlgorithm   
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d046f-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d046f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d046f-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d046f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d046f-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="d046f-110">Attributes</span></span>  
  
|<span data-ttu-id="d046f-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="d046f-111">Attribute</span></span>|<span data-ttu-id="d046f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d046f-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="d046f-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="d046f-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="d046f-114">Especifica se os códigos de hash para cadeias de caracteres são calculados em uma base de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d046f-114">Specifies whether hash codes for strings are calculated on a per application domain basis.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d046f-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="d046f-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="d046f-116">Valor</span><span class="sxs-lookup"><span data-stu-id="d046f-116">Value</span></span>|<span data-ttu-id="d046f-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="d046f-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="d046f-118">O common language runtime não calcula códigos hash para cadeias de caracteres em uma base de domínio de aplicativo; um único algoritmo é usado para calcular códigos hash de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d046f-118">The common language runtime does not compute hash codes for strings on a per application domain basis; a single algorithm is used to calculate string hash codes.</span></span> <span data-ttu-id="d046f-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="d046f-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="d046f-120">O common language runtime computa código hash para cadeias de caracteres em uma base de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d046f-120">The common language runtime computes hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="d046f-121">Cadeias de caracteres idênticas em domínios de aplicativos e processos diferentes terão códigos hash diferentes.</span><span class="sxs-lookup"><span data-stu-id="d046f-121">Identical strings in different application domains and in different processes will have different hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d046f-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d046f-122">Child Elements</span></span>  
 <span data-ttu-id="d046f-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d046f-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d046f-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d046f-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d046f-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="d046f-125">Element</span></span>|<span data-ttu-id="d046f-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="d046f-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d046f-127">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d046f-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d046f-128">Contém informações sobre opções de inicialização do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d046f-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d046f-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="d046f-129">Remarks</span></span>  
 <span data-ttu-id="d046f-130">Por padrão, o <xref:System.StringComparer> classe e o <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> método usar um único algoritmo de hash que gera um código hash consistente entre domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d046f-130">By default, the <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method use a single hashing algorithm that produces a consistent hash code across application domains.</span></span> <span data-ttu-id="d046f-131">Isso equivale a definir as `enabled` atributo do `<UseRandomizedStringHashAlgorithm>` elemento a ser `0`.</span><span class="sxs-lookup"><span data-stu-id="d046f-131">This is equivalent to setting the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `0`.</span></span> <span data-ttu-id="d046f-132">Este é o algoritmo de hash usado no [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d046f-132">This is the hashing algorithm used in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span></span>  
  
 <span data-ttu-id="d046f-133">O <xref:System.StringComparer> classe e o <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> método também pode usar um algoritmo de hash diferente que Compute códigos hash em uma base de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d046f-133">The <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method can also use a different hashing algorithm that computes hash codes on a per application domain basis.</span></span> <span data-ttu-id="d046f-134">Como resultado, os códigos de hash para cadeias de caracteres equivalentes serão diferente entre domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d046f-134">As a result, hash codes for equivalent strings will differ across application domains.</span></span> <span data-ttu-id="d046f-135">Esse é um recurso no consentimento; para tirar proveito dele, você deve definir a `enabled` atributo o `<UseRandomizedStringHashAlgorithm>` elemento a ser `1`.</span><span class="sxs-lookup"><span data-stu-id="d046f-135">This is an opt-in feature; to take advantage of it, you must set the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `1`.</span></span>  
  
 <span data-ttu-id="d046f-136">Normalmente, a pesquisa de cadeia de caracteres em uma tabela de hash é uma operação de (1).</span><span class="sxs-lookup"><span data-stu-id="d046f-136">The string lookup in a hash table is typically an O(1) operation.</span></span> <span data-ttu-id="d046f-137">No entanto, quando um grande número de colisões ocorre, a pesquisa pode se tornar um O (n<sup>2</sup>) operação.</span><span class="sxs-lookup"><span data-stu-id="d046f-137">However, when a large number of collisions occur, the lookup can become an O(n<sup>2</sup>) operation.</span></span> <span data-ttu-id="d046f-138">Você pode usar o `<UseRandomizedStringHashAlgorithm>` elemento de configuração para gerar um algoritmo de hash aleatório por domínio de aplicativo, que por sua vez limita o número de conflitos em potencial, especialmente quando as chaves do qual os códigos de hash são calculados são com base na entrada de dados por usuários.</span><span class="sxs-lookup"><span data-stu-id="d046f-138">You can use the `<UseRandomizedStringHashAlgorithm>` configuration element to generate a random hashing algorithm per application domain, which in turn limits the number of potential collisions, particularly when the keys from which the hash codes are calculated are based on data input by users.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d046f-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d046f-139">Example</span></span>  
 <span data-ttu-id="d046f-140">O exemplo a seguir define uma `DisplayString` classe que inclui uma constante de cadeia de caracteres privados, `s`, cujo valor é "Esta é uma cadeia de caracteres."</span><span class="sxs-lookup"><span data-stu-id="d046f-140">The following example defines a `DisplayString` class that includes a private string constant, `s`, whose value is "This is a string."</span></span> <span data-ttu-id="d046f-141">Ele também inclui um `ShowStringHashCode` método que exibe o valor de cadeia de caracteres e seu código de hash junto com o nome do domínio do aplicativo no qual o método está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="d046f-141">It also includes a `ShowStringHashCode` method that displays the string value and its hash code along with the name of the application domain in which the method is executing.</span></span>  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 <span data-ttu-id="d046f-142">Quando você executar o exemplo sem fornecer um arquivo de configuração, ele exibe a saída semelhante à seguinte.</span><span class="sxs-lookup"><span data-stu-id="d046f-142">When you run the example without supplying a configuration file, it displays output similar to the following.</span></span> <span data-ttu-id="d046f-143">Observe que os códigos hash para a cadeia de caracteres são idênticos em dois domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d046f-143">Note that the hash codes for the string are identical in the two application domains.</span></span>  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 <span data-ttu-id="d046f-144">No entanto, se você adicionar o seguinte arquivo de configuração para o diretório de exemplo e, em seguida, executar o exemplo, os códigos hash para a mesma cadeia de caracteres diferirão de acordo com o domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d046f-144">However, if you add the following configuration file to the example's directory and then run the example, the hash codes for the same string will differ by application domain.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="d046f-145">Quando o arquivo de configuração estiver presente, o exemplo exibe a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="d046f-145">When the configuration file is present, the example displays the following output:</span></span>  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a><span data-ttu-id="d046f-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d046f-146">See also</span></span>
- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
