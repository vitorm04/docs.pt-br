---
title: Executando alterações de maiúsculas e minúsculas que não levam em conta a cultura
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- String.ToLower method
- culture, case sensitivity
- Char.ToLower method
- case, changing in culture-insensitive strings
- Char.ToUpper method
- culture-insensitive string operations, case changes
- String.ToUpper method
- culture parameter
ms.assetid: 822d551c-c69a-4191-82f4-183d82c9179c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 844b0edb93b93704c4886495c673dc0496f7ba71
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44192971"
---
# <a name="performing-culture-insensitive-case-changes"></a><span data-ttu-id="a63b7-102">Executando alterações de maiúsculas e minúsculas que não levam em conta a cultura</span><span class="sxs-lookup"><span data-stu-id="a63b7-102">Performing Culture-Insensitive Case Changes</span></span>
<span data-ttu-id="a63b7-103">Os métodos <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType> e <xref:System.Char.ToLower%2A?displayProperty=nameWithType> fornecem sobrecargas que não aceitam quaisquer parâmetros.</span><span class="sxs-lookup"><span data-stu-id="a63b7-103">The <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods provide overloads that do not accept any parameters.</span></span> <span data-ttu-id="a63b7-104">Por padrão, essas sobrecargas sem parâmetros executam alterações de maiúsculas e minúsculas com base no valor do <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a63b7-104">By default, these overloads without parameters perform case changes based on the value of the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a63b7-105">Isso produz resultados sensíveis a maiúsculas e minúsculas que podem variar de acordo com a cultura.</span><span class="sxs-lookup"><span data-stu-id="a63b7-105">This produces case-sensitive results that can vary by culture.</span></span> <span data-ttu-id="a63b7-106">Para deixar claro se você deseja que as mudanças de maiúsculas e minúsculas sejam sensíveis à cultura ou não sejam insensíveis à cultura, você deve usar as sobrecargas desses métodos que exigem que você especifique explicitamente um parâmetro `culture`.</span><span class="sxs-lookup"><span data-stu-id="a63b7-106">To make it clear whether you want case changes to be culture-sensitive or culture-insensitive, you should use the overloads of these methods that require you to explicitly specify a `culture` parameter.</span></span> <span data-ttu-id="a63b7-107">Para mudanças de maiúsculas e minúsculas sensíveis à cultura, especifique `CultureInfo.CurrentCulture` para o parâmetro `culture`.</span><span class="sxs-lookup"><span data-stu-id="a63b7-107">For culture-sensitive case changes, specify `CultureInfo.CurrentCulture` for the `culture` parameter.</span></span> <span data-ttu-id="a63b7-108">Para mudanças de maiúsculas e minúsculas insensíveis à cultura, especifique `CultureInfo.InvariantCulture` para o parâmetro `culture`.</span><span class="sxs-lookup"><span data-stu-id="a63b7-108">For culture-insensitive case changes, specify `CultureInfo.InvariantCulture` for the `culture` parameter.</span></span>  
  
 <span data-ttu-id="a63b7-109">Muitas vezes, as cadeias de caracteres são convertidas em um formato padrão para permitir uma pesquisa mais fácil.</span><span class="sxs-lookup"><span data-stu-id="a63b7-109">Often, strings are converted to a standard case to enable easier lookup later.</span></span> <span data-ttu-id="a63b7-110">Quando as cadeias de caracteres são usadas dessa maneira, você deve especificar `CultureInfo.InvariantCulture` para o parâmetro `culture`, pois o valor de <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> pode mudar potencialmente entre o tempo que o formato é alterado e o tempo que a pesquisa ocorre.</span><span class="sxs-lookup"><span data-stu-id="a63b7-110">When strings are used in this way, you should specify `CultureInfo.InvariantCulture` for the `culture` parameter, because the value of <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> can potentially change between the time that the case is changed and the time that the lookup occurs.</span></span>  
  
 <span data-ttu-id="a63b7-111">Se uma decisão de segurança é baseada em uma operação de modificação de maiúsculas e minúsculas, a operação deve ser insensível à cultura para garantir que o resultado não seja afetado pelo valor de `CultureInfo.CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="a63b7-111">If a security decision is based on a case change operation, the operation should be culture-insensitive to ensure that the result is not affected by the value of `CultureInfo.CurrentCulture`.</span></span> <span data-ttu-id="a63b7-112">Confira a seção "Comparações de cadeia de caracteres que usam a cultura atual" [Práticas recomendadas para usar cadeias de caracteres](../../../docs/standard/base-types/best-practices-strings.md) para obter um exemplo que demonstra como as operações de cadeias de caracteres que diferenciam a cultura podem produzir resultados inconsistentes.</span><span class="sxs-lookup"><span data-stu-id="a63b7-112">See the "String Comparisons that Use the Current Culture" section of the [Best Practices for Using Strings](../../../docs/standard/base-types/best-practices-strings.md) article for an example that demonstrates how culture-sensitive string operations can produce inconsistent results.</span></span>  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a><span data-ttu-id="a63b7-113">Usando os Métodos String.ToUpper e String.ToLower</span><span class="sxs-lookup"><span data-stu-id="a63b7-113">Using the String.ToUpper and String.ToLower Methods</span></span>  
 <span data-ttu-id="a63b7-114">Para clareza de código, recomenda-se que você sempre use sobrecargas dos métodos `String.ToUpper` e `String.ToLower` que permitem especificar um parâmetro `culture` explicitamente.</span><span class="sxs-lookup"><span data-stu-id="a63b7-114">For code clarity, it is recommended that you always use overloads of the `String.ToUpper` and `String.ToLower` methods that allow you to specify a `culture` parameter explicitly.</span></span> <span data-ttu-id="a63b7-115">Por exemplo, o código a seguir realiza uma pesquisa de identificador.</span><span class="sxs-lookup"><span data-stu-id="a63b7-115">For example, the following code performs an identifier lookup.</span></span> <span data-ttu-id="a63b7-116">A operação `key.ToLower` é sensível à cultura por padrão, mas esse comportamento não fica claro ao ler o código.</span><span class="sxs-lookup"><span data-stu-id="a63b7-116">The `key.ToLower` operation is culture-sensitive by default, but this behavior is not clear from reading the code.</span></span>  
  
### <a name="example"></a><span data-ttu-id="a63b7-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a63b7-117">Example</span></span>  
  
```vb  
Shared Function LookupKey(key As String) As Object  
   Return internalHashtable(key.ToLower())  
End Function  
```  
  
```csharp  
static object LookupKey(string key)   
{  
    return internalHashtable[key.ToLower()];  
}  
```  
  
 <span data-ttu-id="a63b7-118">Se você quiser que a operação `key.ToLower` seja insensível à cultura, você deve alterar o exemplo anterior da seguinte forma para usar explicitamente o `CultureInfo.InvariantCulture` ao mudar a caixa.</span><span class="sxs-lookup"><span data-stu-id="a63b7-118">If you want the `key.ToLower` operation to be culture-insensitive, you should change the preceding example as follows to explicitly use the `CultureInfo.InvariantCulture` when changing the case.</span></span>  
  
```vb  
Shared Function LookupKey(key As String) As Object  
    Return internalHashtable(key.ToLower(CultureInfo.InvariantCulture))  
End Function  
```  
  
```csharp  
static object LookupKey(string key)   
{  
    return internalHashtable[key.ToLower(CultureInfo.InvariantCulture)];  
}  
```  
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a><span data-ttu-id="a63b7-119">Usando os Métodos Char.ToUpper e Char.ToLower</span><span class="sxs-lookup"><span data-stu-id="a63b7-119">Using the Char.ToUpper and Char.ToLower Methods</span></span>  
 <span data-ttu-id="a63b7-120">Embora os métodos `Char.ToUpper` e `Char.ToLower` tenham as mesmas características que os métodos `String.ToUpper` e `String.ToLower`, as únicas culturas afetadas são turca (Turquia) e azerbaijana (Latino, Azerbaijão).</span><span class="sxs-lookup"><span data-stu-id="a63b7-120">Although the `Char.ToUpper` and `Char.ToLower` methods have the same characteristics as the `String.ToUpper` and `String.ToLower` methods, the only cultures that are affected are Turkish (Turkey) and Azerbaijani (Latin, Azerbaijan).</span></span> <span data-ttu-id="a63b7-121">Essas são apenas duas culturas com diferenças de maiúsculas e minúsculas de um único caractere.</span><span class="sxs-lookup"><span data-stu-id="a63b7-121">These are the only two cultures with single-character casing differences.</span></span> <span data-ttu-id="a63b7-122">Para obter mais detalhes sobre este mapeamento de maiúsculas e minúsculas único, confira a seção "Maiúsculas e minúsculas" no tópico da classe <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a63b7-122">For more details about this unique case mapping, see the "Casing" section in the <xref:System.String> class topic.</span></span> <span data-ttu-id="a63b7-123">Para clareza de código e para garantir resultados consistentes, recomenda-se que você sempre use as sobrecargas desses métodos que permitem que você especifique explicitamente um parâmetro `culture`.</span><span class="sxs-lookup"><span data-stu-id="a63b7-123">For code clarity and to ensure consistent results, it is recommended that you always use the overloads of these methods that allow you to explicitly specify a `culture` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a63b7-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a63b7-124">See also</span></span>

- <xref:System.String.ToUpper%2A?displayProperty=nameWithType>  
- <xref:System.String.ToLower%2A?displayProperty=nameWithType>  
- <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>  
- <xref:System.Char.ToLower%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="a63b7-125">Executando operações de cadeia de caracteres que não levam em conta a cultura</span><span class="sxs-lookup"><span data-stu-id="a63b7-125">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
