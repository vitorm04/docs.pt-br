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
ms.openlocfilehash: 148d55c8b8a63737867c4bfdf3ab118dfdefd6f9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174089"
---
# <a name="userandomizedstringhashalgorithm-element"></a><span data-ttu-id="cf929-102">Elemento \<UseRandomizedStringHashAlgorithm></span><span class="sxs-lookup"><span data-stu-id="cf929-102">\<UseRandomizedStringHashAlgorithm> Element</span></span>

<span data-ttu-id="cf929-103">Determina se o Common Language Runtime calcula códigos de hash para cadeias de caracteres por aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf929-103">Determines whether the common language runtime calculates hash codes for strings on a per application domain basis.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<UseRandomizedStringHashAlgorithm>**  
  
## <a name="syntax"></a><span data-ttu-id="cf929-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cf929-104">Syntax</span></span>  
  
```xml  
<UseRandomizedStringHashAlgorithm
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf929-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cf929-105">Attributes and Elements</span></span>  

 <span data-ttu-id="cf929-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cf929-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf929-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="cf929-107">Attributes</span></span>  
  
|<span data-ttu-id="cf929-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="cf929-108">Attribute</span></span>|<span data-ttu-id="cf929-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="cf929-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="cf929-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="cf929-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="cf929-111">Especifica se os códigos de hash para cadeias de caracteres são calculados em uma base de domínio por aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf929-111">Specifies whether hash codes for strings are calculated on a per application domain basis.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="cf929-112">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="cf929-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="cf929-113">Valor</span><span class="sxs-lookup"><span data-stu-id="cf929-113">Value</span></span>|<span data-ttu-id="cf929-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="cf929-114">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="cf929-115">O Common Language Runtime não computa códigos hash para cadeias de caracteres por aplicativo; um único algoritmo é usado para calcular códigos de hash de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="cf929-115">The common language runtime does not compute hash codes for strings on a per application domain basis; a single algorithm is used to calculate string hash codes.</span></span> <span data-ttu-id="cf929-116">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="cf929-116">This is the default.</span></span>|  
|`1`|<span data-ttu-id="cf929-117">O Common Language Runtime computa códigos de hash para cadeias de caracteres por aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf929-117">The common language runtime computes hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="cf929-118">Cadeias de caracteres idênticas em domínios de aplicativo diferentes e em processos diferentes terão códigos de hash diferentes.</span><span class="sxs-lookup"><span data-stu-id="cf929-118">Identical strings in different application domains and in different processes will have different hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cf929-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cf929-119">Child Elements</span></span>  

 <span data-ttu-id="cf929-120">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="cf929-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cf929-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cf929-121">Parent Elements</span></span>  
  
|<span data-ttu-id="cf929-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="cf929-122">Element</span></span>|<span data-ttu-id="cf929-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="cf929-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cf929-124">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cf929-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="cf929-125">Contém informações sobre opções de inicialização do runtime.</span><span class="sxs-lookup"><span data-stu-id="cf929-125">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf929-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="cf929-126">Remarks</span></span>  

 <span data-ttu-id="cf929-127">Por padrão, a <xref:System.StringComparer> classe e o <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> método usam um único algoritmo de hash que produz um código hash consistente entre domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf929-127">By default, the <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method use a single hashing algorithm that produces a consistent hash code across application domains.</span></span> <span data-ttu-id="cf929-128">Isso é equivalente a definir o `enabled` atributo do `<UseRandomizedStringHashAlgorithm>` elemento como `0` .</span><span class="sxs-lookup"><span data-stu-id="cf929-128">This is equivalent to setting the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `0`.</span></span> <span data-ttu-id="cf929-129">Esse é o algoritmo de hash usado no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="cf929-129">This is the hashing algorithm used in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="cf929-130">A <xref:System.StringComparer> classe e o <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> método também podem usar um algoritmo de hash diferente que computa códigos de hash em uma base de domínio por aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf929-130">The <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method can also use a different hashing algorithm that computes hash codes on a per application domain basis.</span></span> <span data-ttu-id="cf929-131">Como resultado, os códigos de hash para cadeias de caracteres equivalentes serão diferentes entre domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf929-131">As a result, hash codes for equivalent strings will differ across application domains.</span></span> <span data-ttu-id="cf929-132">Esse é um recurso opcional; para aproveitar isso, você deve definir o `enabled` atributo do `<UseRandomizedStringHashAlgorithm>` elemento como `1` .</span><span class="sxs-lookup"><span data-stu-id="cf929-132">This is an opt-in feature; to take advantage of it, you must set the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `1`.</span></span>  
  
 <span data-ttu-id="cf929-133">A pesquisa de cadeia de caracteres em uma tabela de hash normalmente é uma operação O (1).</span><span class="sxs-lookup"><span data-stu-id="cf929-133">The string lookup in a hash table is typically an O(1) operation.</span></span> <span data-ttu-id="cf929-134">No entanto, quando ocorre um grande número de colisões, a pesquisa pode se tornar uma operação O (n<sup>2</sup>).</span><span class="sxs-lookup"><span data-stu-id="cf929-134">However, when a large number of collisions occur, the lookup can become an O(n<sup>2</sup>) operation.</span></span> <span data-ttu-id="cf929-135">Você pode usar o `<UseRandomizedStringHashAlgorithm>` elemento de configuração para gerar um algoritmo de hash aleatório por domínio de aplicativo, que, por sua vez, limita o número de colisões em potencial, especialmente quando as chaves das quais os códigos de hash são calculados se baseiam na entrada de dados pelos usuários.</span><span class="sxs-lookup"><span data-stu-id="cf929-135">You can use the `<UseRandomizedStringHashAlgorithm>` configuration element to generate a random hashing algorithm per application domain, which in turn limits the number of potential collisions, particularly when the keys from which the hash codes are calculated are based on data input by users.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf929-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cf929-136">Example</span></span>  

 <span data-ttu-id="cf929-137">O exemplo a seguir define uma `DisplayString` classe que inclui uma constante de cadeia de caracteres privada, `s` , cujo valor é "esta é uma cadeia de caracteres".</span><span class="sxs-lookup"><span data-stu-id="cf929-137">The following example defines a `DisplayString` class that includes a private string constant, `s`, whose value is "This is a string."</span></span> <span data-ttu-id="cf929-138">Também inclui um método `ShowStringHashCode` que exibe o valor de cadeia de caracteres e seu código de hash com o nome do domínio do aplicativo no qual o método está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="cf929-138">It also includes a `ShowStringHashCode` method that displays the string value and its hash code along with the name of the application domain in which the method is executing.</span></span>  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 <span data-ttu-id="cf929-139">Quando você executa o exemplo sem fornecer um arquivo de configuração, ele exibe uma saída semelhante à seguinte.</span><span class="sxs-lookup"><span data-stu-id="cf929-139">When you run the example without supplying a configuration file, it displays output similar to the following.</span></span> <span data-ttu-id="cf929-140">Observe que os códigos hash para a cadeia de caracteres são idênticos nos dois domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf929-140">Note that the hash codes for the string are identical in the two application domains.</span></span>  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 <span data-ttu-id="cf929-141">Entretanto, se você adicionar o seguinte arquivo de configuração ao diretório de exemplo e, então, executar o exemplo, os códigos hash da mesma cadeia de caracteres diferirão de acordo com o domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf929-141">However, if you add the following configuration file to the example's directory and then run the example, the hash codes for the same string will differ by application domain.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="cf929-142">Quando o arquivo de configuração estiver presente, o exemplo exibe a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="cf929-142">When the configuration file is present, the example displays the following output:</span></span>  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a><span data-ttu-id="cf929-143">Confira também</span><span class="sxs-lookup"><span data-stu-id="cf929-143">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
