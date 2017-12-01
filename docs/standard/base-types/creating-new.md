---
title: Criando novas cadeias de caracteres no .NET
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
- CopyTo method
- Join method
- Format method
- Concat method
- strings [.NET Framework], creating
- Insert method
ms.assetid: 06fdf123-2fac-4459-8904-eb48ab908a30
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d000cd88fc9ee9fd48ef25e9bb4982688564a2a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-new-strings-in-net"></a>Criando novas cadeias de caracteres no .NET
O [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] permite que cadeias de caracteres a ser criada usando atribuição simples e também sobrecarrega um construtor de classe para dar suporte à criação de cadeia de caracteres usando um número de parâmetros diferentes. O [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] também fornece vários métodos de <xref:System.String?displayProperty=nameWithType> classe que criar a nova cadeia de objetos, combinando várias cadeias de caracteres, matrizes de cadeias de caracteres ou objetos.  
  
## <a name="creating-strings-using-assignment"></a>Criando cadeias de caracteres usando atribuição  
 A maneira mais fácil de criar um novo <xref:System.String> objeto é simplesmente atribuir uma cadeia de caracteres literal a uma <xref:System.String> objeto.  
  
## <a name="creating-strings-using-a-class-constructor"></a>Criando cadeias de caracteres usando um construtor de classe  
 Você pode usar as sobrecargas do <xref:System.String> construtor de classe para criar cadeias de caracteres de matrizes de caracteres. Você também pode criar uma nova cadeia de caracteres duplicando um caractere específico, m número de vezes especificado.  
  
## <a name="methods-that-return-strings"></a>Métodos que retornam cadeias de caracteres  
 A tabela a seguir lista vários métodos úteis que retornam novos objetos de cadeia de caracteres.  
  
|Nome do método|Use|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|Cria uma cadeia de caracteres formatada de um conjunto de objetos de entrada.|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|Cria cadeias de caracteres de duas ou mais cadeias de caracteres.|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|Cria uma nova cadeia de caracteres combinando uma matriz de cadeias de caracteres.|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|Cria uma nova cadeia de caracteres inserindo uma cadeia de caracteres no índice especificado de uma cadeia de caracteres existente.|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|Copia caracteres especificados de uma cadeia de caracteres para uma posição especificada em uma matriz de caracteres.|  
  
### <a name="format"></a>Formatar  
 Você pode usar o **Format** método para criar cadeias de caracteres formatadas e concatenar cadeias de caracteres que representa os vários objetos. Este método converte automaticamente qualquer objeto passado em uma cadeia de caracteres. Por exemplo, se seu aplicativo deve exibir um **Int32** valor e um **DateTime** valor para o usuário, você pode facilmente construir uma cadeia de caracteres para representar esses valores usando o **formato**método. Para obter informações sobre as convenções de formatação usadas com esse método, consulte a seção sobre [formatação de composição](../../../docs/standard/base-types/composite-formatting.md).  
  
 O exemplo a seguir usa o **formato** método para criar uma cadeia de caracteres que usa uma variável de inteiro.  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 Neste exemplo,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> exibe a data e hora atuais da maneira especificada pela cultura associada ao thread atual.  
  
### <a name="concat"></a>Concat  
 O **concat** método pode ser usado para criar facilmente um novo objeto de cadeia de caracteres de dois ou mais objetos existentes. Ele fornece uma maneira independente da linguagem para concatenar cadeias de caracteres. Esse método aceita qualquer classe que deriva de **Object**. O exemplo a seguir cria uma cadeia de caracteres de dois objetos de cadeia de caracteres existentes e um caractere de separação.  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a>Join  
 O **JOIN** método cria uma nova cadeia de caracteres de uma matriz de cadeias de caracteres e uma cadeia de caracteres do separador. Esse método é útil se você quiser concatenar várias cadeias de caracteres fazendo uma lista, talvez separada por vírgula.  
  
 O exemplo a seguir usa um espaço para associar uma matriz de cadeias de caracteres.  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a>Inserir  
 O **String. Insert** método cria uma nova cadeia de caracteres inserindo uma cadeia de caracteres em uma posição especificada em outra cadeia de caracteres. Este método usa um índice baseado em zero. O exemplo a seguir insere uma cadeia de caracteres na quinta posição do índice de `MyString` e cria uma nova cadeia de caracteres com esse valor.  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a>CopyTo  
 O **String.CopyTo** método copia partes de uma cadeia de caracteres em uma matriz de caracteres. Você pode especificar o índice inicial da cadeia de caracteres e o número de caracteres a serem copiados. Este método usa o índice de origem, uma matriz de caracteres, o índice de destino e o número de caracteres a serem copiados. Todos os índices são baseados em zero.  
  
 O exemplo a seguir usa o **CopyTo** método para copiar os caracteres da palavra "Hello" de uma cadeia de caracteres do objeto para a primeira posição de índice de uma matriz de caracteres.  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a>Consulte também  
 [Operações básicas de cadeias de caracteres](../../../docs/standard/base-types/basic-string-operations.md)  
 [Formatação de composição](../../../docs/standard/base-types/composite-formatting.md)
