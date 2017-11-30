---
title: Usando a classe StringBuilder no .NET
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
- cpp
helpviewer_keywords:
- Remove method
- strings [.NET Framework], capacities
- StringBuilder object
- Replace method
- AppendFormat method
- Append method
- Insert method
- strings [.NET Framework], StringBuilder object
ms.assetid: 5c14867c-9a99-45bc-ae7f-2686700d377a
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3a6c8f6dee9f2a1da6ed4a8219c1b4832464d9aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="using-the-stringbuilder-class-in-net"></a>Usando a classe StringBuilder no .NET
O <xref:System.String> objeto é imutável. Toda vez que você usar um dos métodos na <xref:System.String?displayProperty=nameWithType> classe, que você cria um novo objeto de cadeia de caracteres na memória, o que requer uma nova alocação de espaço para esse novo objeto. Em situações em que você precisa realizar repetidas modificações em uma cadeia de caracteres, a sobrecarga associada à criação de um novo <xref:System.String> objeto pode ser caro. O <xref:System.Text.StringBuilder?displayProperty=nameWithType> classe pode ser usada quando você deseja modificar uma cadeia de caracteres sem criar um novo objeto. Por exemplo, usando o <xref:System.Text.StringBuilder> classe pode melhorar o desempenho ao concatenar várias cadeias de caracteres juntas em um loop.  
  
## <a name="importing-the-systemtext-namespace"></a>Importando o namespace System.Text  
 O <xref:System.Text.StringBuilder> classe é encontrada no <xref:System.Text> namespace.  Para evitar ter que fornecer um nome de tipo totalmente qualificado no seu código, você pode importar o <xref:System.Text> namespace:  
  
 [!code-cpp[Conceptual.StringBuilder#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#11)]
 [!code-csharp[Conceptual.StringBuilder#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#11)]
 [!code-vb[Conceptual.StringBuilder#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#11)]  
  
## <a name="instantiating-a-stringbuilder-object"></a>Criando uma instância de um objeto StringBuilder  
 Você pode criar uma nova instância do <xref:System.Text.StringBuilder> classe inicializando sua variável com um dos métodos sobrecarregados do construtor, conforme ilustrado no exemplo a seguir.  
  
 [!code-cpp[Conceptual.StringBuilder#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#1)]
 [!code-csharp[Conceptual.StringBuilder#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#1)]
 [!code-vb[Conceptual.StringBuilder#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#1)]  
  
## <a name="setting-the-capacity-and-length"></a>Definindo a capacidade e o comprimento  
 Embora o <xref:System.Text.StringBuilder> é um objeto dinâmico que permite que você expanda o número de caracteres na cadeia de caracteres que ele encapsula, você pode especificar um valor para o número máximo de caracteres que pode conter. Esse valor é chamado a capacidade do objeto e não deve ser confundido com o comprimento da cadeia de caracteres que o atual <xref:System.Text.StringBuilder> contém. Por exemplo, você pode criar uma nova instância do <xref:System.Text.StringBuilder> classe com a cadeia de caracteres "Hello", que tem um comprimento de 5 e você pode especificar que o objeto tem uma capacidade máxima de 25. Quando você modifica o <xref:System.Text.StringBuilder>, ele não realocar tamanho para si mesmo, até que a capacidade for atingida. Quando isso ocorre, o novo espaço é alocado automaticamente e a capacidade é dobrada. Você pode especificar a capacidade do <xref:System.Text.StringBuilder> classe usando um dos construtores sobrecarregados. O exemplo a seguir especifica que o objeto `MyStringBuilder` pode ser expandido para um máximo de 25 espaços.  
  
 [!code-cpp[Conceptual.StringBuilder#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#2)]
 [!code-csharp[Conceptual.StringBuilder#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#2)]
 [!code-vb[Conceptual.StringBuilder#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#2)]  
  
 Além disso, você pode usar a leitura/gravação <xref:System.Text.StringBuilder.Capacity%2A> propriedade para definir o comprimento máximo de seu objeto. O exemplo a seguir usa a propriedade **Capacidade** para definir o comprimento máximo de objeto.  
  
 [!code-cpp[Conceptual.StringBuilder#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#3)]
 [!code-csharp[Conceptual.StringBuilder#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#3)]
 [!code-vb[Conceptual.StringBuilder#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#3)]  
  
 O <xref:System.Text.StringBuilder.EnsureCapacity%2A> método pode ser usado para verificar a capacidade do atual **StringBuilder**. Se a capacidade for maior que o valor transmitido, nenhuma alteração é feita; no entanto, se a capacidade for menor do que o valor transmitido, a capacidade atual é alterada para corresponder ao valor transmitido.  
  
 O <xref:System.Text.StringBuilder.Length%2A> propriedade também pode ser exibida ou definida. Se você definir a propriedade **Comprimento** para um valor maior que a propriedade **Capacidade**, a propriedade **Capacidade** será alterada automaticamente para o mesmo valor que a propriedade **Comprimento**. Definir a propriedade **Comprimento** para um valor menor que o comprimento da cadeia de caracteres no **StringBuilder** atual, diminui a cadeia de caracteres.  
  
## <a name="modifying-the-stringbuilder-string"></a>Modificando a cadeia de caracteres do StringBuilder  
 A tabela a seguir lista os métodos que você pode usar para modificar o conteúdo de um **StringBuilder**.  
  
|Nome do método|Use|  
|-----------------|---------|  
|<xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>|Acrescenta informações ao final do **StringBuilder** atual.|  
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|Substitui um especificador de formato transmitido em uma cadeia de caracteres com texto formatado.|  
|<xref:System.Text.StringBuilder.Insert%2A?displayProperty=nameWithType>|Insere uma cadeia de caracteres ou um objeto no índice especificado do **StringBuilder** atual.|  
|<xref:System.Text.StringBuilder.Remove%2A?displayProperty=nameWithType>|Remove um número especificado de caracteres do **StringBuilder** atual.|  
|<xref:System.Text.StringBuilder.Replace%2A?displayProperty=nameWithType>|Substitui um caractere especificado em um índice especificado.|  
  
### <a name="append"></a>Acrescentar  
 O **Append** método pode ser usado para adicionar texto ou uma representação de cadeia de caracteres de um objeto ao final de uma cadeia de caracteres representado por atual **StringBuilder**. O exemplo a seguir inicializa um **StringBuilder** para "Hello World" e, em seguida, acrescenta algum texto ao final do objeto. Espaço é alocado automaticamente conforme necessário.  
  
 [!code-cpp[Conceptual.StringBuilder#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#4)]
 [!code-csharp[Conceptual.StringBuilder#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#4)]
 [!code-vb[Conceptual.StringBuilder#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#4)]  
  
### <a name="appendformat"></a>AppendFormat  
 O <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> método adiciona texto ao final do <xref:System.Text.StringBuilder> objeto. Ele dá suporte ao recurso de formatação composta (para obter mais informações, consulte [formatação composta](../../../docs/standard/base-types/composite-formatting.md)) chamando o <xref:System.IFormattable> implementação do objeto ou objetos a serem formatados. Portanto, aceita as cadeias de caracteres de formato padrão para valores numéricos, data e hora e enumeração, cadeias de caracteres de formato personalizado para valores numéricos e de data e hora e cadeias de caracteres de formato definidas para tipos personalizados. (Para obter informações sobre a formatação, consulte [Formatando tipos](../../../docs/standard/base-types/formatting-types.md).) Você pode usar esse método para personalizar o formato de variáveis e acrescente esses valores para um <xref:System.Text.StringBuilder>. O exemplo a seguir usa o <xref:System.Text.StringBuilder.AppendFormat%2A> método para colocar um valor inteiro formatado como um valor de moeda no final de uma <xref:System.Text.StringBuilder> objeto.  
  
 [!code-cpp[Conceptual.StringBuilder#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#5)]
 [!code-csharp[Conceptual.StringBuilder#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#5)]
 [!code-vb[Conceptual.StringBuilder#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#5)]  
  
### <a name="insert"></a>Inserir  
 O <xref:System.Text.StringBuilder.Insert%2A> método adiciona uma cadeia de caracteres ou objeto para uma posição especificada na atual <xref:System.Text.StringBuilder> objeto. O exemplo a seguir usa esse método para inserir uma palavra na sexta posição de um <xref:System.Text.StringBuilder> objeto.  
  
 [!code-cpp[Conceptual.StringBuilder#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#6)]
 [!code-csharp[Conceptual.StringBuilder#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#6)]
 [!code-vb[Conceptual.StringBuilder#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#6)]  
  
### <a name="remove"></a>Remover  
 Você pode usar o **remover** método para remover um número especificado de caracteres do atual <xref:System.Text.StringBuilder> objeto, começando em um índice de base zero especificado. O exemplo a seguir usa o **remover** método para reduzir um <xref:System.Text.StringBuilder> objeto.  
  
 [!code-cpp[Conceptual.StringBuilder#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#7)]
 [!code-csharp[Conceptual.StringBuilder#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#7)]
 [!code-vb[Conceptual.StringBuilder#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#7)]  
  
### <a name="replace"></a>Substituir  
 O **substituir** método pode ser usado para substituir caracteres dentro de <xref:System.Text.StringBuilder> especificado de objeto com outro caractere. O exemplo a seguir usa o **substituir** método para pesquisar um <xref:System.Text.StringBuilder> todas as instâncias do ponto de exclamação (!) de caracteres e substituí-los com o caractere de ponto de interrogação (?) do objeto.  
  
 [!code-cpp[Conceptual.StringBuilder#8](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#8)]
 [!code-csharp[Conceptual.StringBuilder#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#8)]
 [!code-vb[Conceptual.StringBuilder#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#8)]  
  
## <a name="converting-a-stringbuilder-object-to-a-string"></a>Convertendo um objeto StringBuilder em uma cadeia de caracteres  
 Você deve converter o <xref:System.Text.StringBuilder> o objeto para um <xref:System.String> objeto antes que você pode passar a cadeia de caracteres representada pelo <xref:System.Text.StringBuilder> objeto para um método que tem um <xref:System.String> parâmetro ou exibi-lo na interface do usuário. Fazer essa conversão ao chamar o <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> método. O exemplo a seguir chama um número de <xref:System.Text.StringBuilder> métodos e, em seguida, chama o <xref:System.Text.StringBuilder.ToString?displayProperty=nameWithType> método para exibir a cadeia de caracteres.  
  
 [!code-csharp[Conceptual.StringBuilder#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/tostringexample1.cs#10)]
 [!code-vb[Conceptual.StringBuilder#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/tostringexample1.vb#10)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Text.StringBuilder?displayProperty=nameWithType>  
 [Operações básicas de cadeias de caracteres](../../../docs/standard/base-types/basic-string-operations.md)  
 [Formatando Tipos](../../../docs/standard/base-types/formatting-types.md)
