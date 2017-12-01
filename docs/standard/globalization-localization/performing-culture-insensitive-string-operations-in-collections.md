---
title: "Executando operações de cadeia de caracteres que não levam em conta a cultura em coleções"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CaseInsensitiveComparer class, using
- CollectionsUtil.CreateCaseInsensitiveHashtable method
- culture-insensitive string operations, collections
- collections [.NET Framework], culture-insensitive string operations
- CaseInsensitiveHashCodeProvider class, using
- ArrayList.Sort method
- SortedList class, culture-insensitive string operations
- culture parameter
ms.assetid: 5cdc9396-a64b-4615-a1cd-b605db4c5983
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a1ecba9c055f8e99d26283c7f37c2430dc17bf31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a>Executando operações de cadeia de caracteres que não levam em conta a cultura em coleções
Há classes e membros de <xref:System.Collections> namespace que fornece o comportamento de sensíveis à cultura por padrão. Os construtores padrão para o <xref:System.Collections.CaseInsensitiveComparer> e <xref:System.Collections.CaseInsensitiveHashCodeProvider> classes inicializar uma nova instância usando o <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> propriedade. Todas as sobrecargas do <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> método cria uma nova instância do <xref:System.Collections.Hashtable> classe usando o `Thread.CurrentCulture` propriedade por padrão. Sobrecargas do <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> método executa classificações de cultura usando padrão `Thread.CurrentCulture`. Classificação e pesquisa em uma <xref:System.Collections.SortedList> pode ser afetado por `Thread.CurrentCulture` quando as cadeias de caracteres são usadas como as chaves. Siga as recomendações de uso fornecidas nesta seção para obter os resultados não levam em conta a cultura de classes e métodos de `Collections` namespace.  
  
 **Observação** passando <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> para uma comparação método realizar uma comparação sem diferenciação de cultura. No entanto, ele não causa uma comparação não linguística, por exemplo, para caminhos de arquivos, chaves do registro e variáveis de ambiente. Não oferece suporte a decisões de segurança com base no resultado da comparação. Para obter uma comparação não linguística ou suporte para decisões de segurança com base no resultado, o aplicativo deve usar um método de comparação que aceita um <xref:System.StringComparison> valor. O aplicativo deve passar <xref:System.StringComparison>.  
  
## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a>Usando as Classes de CaseInsensitiveHashCodeProvider e CaseInsensitiveComparer  
 Os construtores padrão `CaseInsensitiveHashCodeProvider` e `CaseInsensitiveComparer` inicializar uma nova instância da classe usando o `Thread.CurrentCulture`, resultando no comportamento sensíveis à cultura. O exemplo de código a seguir demonstra o construtor para um `Hashtable` que é sensíveis à cultura, pois ele usa os construtores padrão `CaseInsensitiveHashCodeProvider` e `CaseInsensitiveComparer`.  
  
```vb  
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)  
```  
  
```csharp  
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);  
```  
  
 Se você quiser criar uma cultura não diferencia `Hashtable` usando o `CaseInsensitiveComparer` e `CaseInsensitiveHashCodeProvider` classes, inicializar novas instâncias dessas classes usando os construtores que aceitam um `culture` parâmetro. Para o `culture` parâmetro, especifique <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. O exemplo de código a seguir demonstra o construtor para uma cultura não diferencia `Hashtable`.  
  
```vb  
internalHashtable = New Hashtable(New  
    CaseInsensitiveHashCodeProvider(CultureInfo.InvariantCulture),  
    New CaseInsensitiveComparer(CultureInfo.InvariantCulture))  
```  
  
```csharp  
internalHashtable = new Hashtable(new CaseInsensitiveHashCodeProvider  
    (CultureInfo.InvariantCulture),   
    new CaseInsensitiveComparer(CultureInfo.InvariantCulture));  
```  
  
## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a>Usando o método CollectionsUtil  
 O `CollectionsUtil.CreateCaseInsensitiveHashTable` método é um atalho útil para criar uma nova instância do `Hashtable` classe que diferencia maiusculas de minúsculas de cadeias de caracteres. No entanto, todas as sobrecargas do `CollectionsUtil.CreateCaseInsensitiveHashTable` método são sensíveis à cultura, porque eles usam o `Thread.CurrentCulture` propriedade. Não é possível criar uma cultura não diferencia `Hashtable` usando esse método. Para criar uma cultura não diferencia `Hashtable`, use o `Hashtable` construtor que aceite um `culture` parâmetro. Para o `culture` parâmetro, especifique `CultureInfo.InvariantCulture`. O exemplo de código a seguir demonstra o construtor para uma cultura não diferencia `Hashtable`.  
  
```vb  
internalHashtable = New Hashtable(New  
    CaseInsensitiveHashCodeProvider(CultureInfo.InvariantCulture),  
    New CaseInsensitiveComparer(CultureInfo.InvariantCulture))  
```  
  
```csharp  
internalHashtable = new Hashtable(new CaseInsensitiveHashCodeProvider  
    (CultureInfo.InvariantCulture),   
    new CaseInsensitiveComparer(CultureInfo.InvariantCulture));  
```  
  
<a name="cpconperformingculture-insensitivestringoperationsincollectionsanchor1"></a>   
## <a name="using-the-sortedlist-class"></a>Usando a classe SortedList  
 Um `SortedList` representa uma coleção de pares chave-valor que são classificados pelas chaves e são acessíveis por chave e por índice. Quando você usa um `SortedList` onde as chaves de cadeias de caracteres, a classificação e a pesquisa podem ser afetados pelo `Thread.CurrentCulture` propriedade. Para obter o comportamento de cultura de um `SortedList`, crie um `SortedList` usando um dos construtores que aceita um `comparer` parâmetro. O `comparer` parâmetro especifica o <xref:System.Collections.IComparer> implementação para uso na comparação entre chaves. Para o parâmetro, especifique uma classe de comparador personalizado que usa `CultureInfo.InvariantCulture` para comparar as chaves. O exemplo a seguir ilustra uma classe de comparador sem diferenciação de cultura personalizada que você pode especificar como o `comparer` parâmetro para um `SortedList` construtor.  
  
```vb  
Imports System  
Imports System.Collections  
Imports System.Globalization  
  
Friend Class InvariantComparer  
    Implements IComparer   
    Private m_compareInfo As CompareInfo  
    Friend Shared [Default] As New InvariantComparer()  
  
    Friend Sub New()  
        m_compareInfo = CultureInfo.InvariantCulture.CompareInfo  
    End Sub     
  
    Public Function Compare(a As Object, b As Object) As Integer _  
            Implements IComparer.Compare  
        Dim sa As String = CType(a, String)  
        Dim sb As String = CType(b, String)  
        If Not (sa Is Nothing) And Not (sb Is Nothing) Then  
            Return m_compareInfo.Compare(sa, sb)  
        Else  
            Return Comparer.Default.Compare(a, b)  
        End If  
    End Function  
End Class  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Globalization;  
  
internal class InvariantComparer : IComparer   
{  
    private CompareInfo m_compareInfo;  
    internal static readonly InvariantComparer Default = new  
        InvariantComparer();  
  
    internal InvariantComparer()   
    {  
        m_compareInfo = CultureInfo.InvariantCulture.CompareInfo;  
    }  
  
    public int Compare(Object a, Object b)  
    {  
        String sa = a as String;  
        String sb = b as String;  
        if (sa != null && sb != null)  
            return m_compareInfo.Compare(sa, sb);  
        else  
            return Comparer.Default.Compare(a,b);  
    }  
}  
```  
  
 Em geral, se você usar um `SortedList` em cadeias de caracteres sem especificar um comparador personalizado invariável, uma alteração `Thread.CurrentCulture` depois que a lista foi preenchida pode invalidar a lista.  
  
## <a name="using-the-arraylistsort-method"></a>Usando o método ArrayList  
 Sobrecargas do `ArrayList.Sort` método executa classificações de sensíveis à cultura por padrão usando o `Thread.CurrentCulture` propriedade. Podem variar com a cultura devido a diferentes ordens de classificação. Para eliminar o comportamento de sensíveis à cultura, use as sobrecargas do método que aceitem um `IComparer` implementação. Para o `comparer` parâmetro, especifique uma classe de comparador invariável personalizado que usa `CultureInfo.InvariantCulture`. Um exemplo de uma classe personalizada comparador invariável é fornecido no [usando a classe SortedList](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) tópico.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Collections.CaseInsensitiveComparer>  
 <xref:System.Collections.CaseInsensitiveHashCodeProvider>  
 <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Collections.SortedList>  
 <xref:System.Collections.Hashtable>  
 <xref:System.Collections.IComparer>  
 [Executando operações de cadeia de caracteres que não levam em conta a cultura](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)  
 <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
