---
title: Manipulando valores nulos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: 9c0b6d250dcedc9b5996c50ccdb2f183707e54e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33364265"
---
# <a name="handling-null-values"></a>Manipulando valores nulos
Um valor nulo em um banco de dados relacional é usado quando o valor em uma coluna é desconhecido ou ausente. Um nulo não é uma cadeia de caracteres vazia (para os tipos de dados character ou datetime) nem um valor zero (para tipos de dados numéricos). A especificação ANSI SQL-92 indica que um valor nulo deve ser o mesmo para todos os tipos de dados, para que todos os nulos sejam tratados consistentemente. O namespace <xref:System.Data.SqlTypes> fornece uma semântica nula implementando a interface <xref:System.Data.SqlTypes.INullable>. Cada um dos tipos de dados no <xref:System.Data.SqlTypes> tem sua própria propriedade `IsNull` e um valor `Null` que pode ser atribuído a uma instância desse tipo de dados.  
  
> [!NOTE]
>  O .NET Framework versão 2.0 incorporou o suporte a tipos que permitem valores nulos, proporcionando aos programadores meios de estender um tipo de valor para representar todos os valores do tipo subjacente. Esses tipos CLR que permitem valores nulos representam uma instância da estrutura <xref:System.Nullable>. Esse recurso é especialmente útil quando os tipos de valor são boxed e unboxed, fornecendo uma compatibilidade aprimorada com os tipos de objeto. Os tipos CLR que permitem valores nulos não se destinam ao armazenamento dos valores nulos do banco de dados, pois um valor nulo ANSI SQL não se comporta da mesma maneira que uma referência `null` (ou `Nothing` no Visual Basic). Para trabalhar com valores nulos ANSI SQL do banco de dados, use os valores nulos <xref:System.Data.SqlTypes>, em vez de <xref:System.Nullable>. Para obter mais informações sobre como trabalhar com CLR tipos anuláveis no Visual Basic consulte [tipos de valor anuláveis](~/docs/visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)e para c#, consulte [usando tipos anuláveis](~/docs/csharp/programming-guide/nullable-types/using-nullable-types.md).  
  
## <a name="nulls-and-three-valued-logic"></a>Valores nulos e lógica de três valores  
 A permissão de valores nulos em definições de coluna incorpora a lógica de três valores no aplicativo. Uma comparação pode ser avaliada como uma das três condições:  
  
-   verdadeiro  
  
-   False  
  
-   Unknown  
  
 Como o valor número é considerado desconhecido, dois valores nulos comparados entre si não são considerados iguais. Nas expressões que usam operadores aritméticos, se qualquer um dos operandos for nulo, o resultado também será nulo.  
  
## <a name="nulls-and-sqlboolean"></a>Valores nulos e SqlBoolean  
 A comparação entre qualquer <xref:System.Data.SqlTypes> retornará <xref:System.Data.SqlTypes.SqlBoolean>. A função `IsNull` de cada `SqlType` retornará <xref:System.Data.SqlTypes.SqlBoolean> e poderá ser usada para verificar valores nulos. As seguintes tabelas da verdade mostram como os operadores AND, OR e NO funcionam na presença de um valor nulo. (T=verdadeiro, F=falso e U=desconhecido ou nulo.)  
  
 ![Tabela verdade](../../../../../docs/framework/data/adonet/sql/media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")  
  
### <a name="understanding-the-ansinulls-option"></a>Noções básicas sobre a opção ANSI_NULLS  
 <xref:System.Data.SqlTypes> fornece a mesma semântica do que a proporcionada quando a opção ANSI_NULLS é definida no SQL Server. Todos os operadores aritméticos (+, -, *, /, %), operadores bit a bit (~, &, &#124;), e a maioria das funções de retorno nulo se qualquer um dos operandos ou argumentos for null, exceto para a propriedade `IsNull`.  
  
 O padrão ANSI SQL-92 não suporta *columnName* = NULL em uma cláusula WHERE. No SQL Server, a opção ANSI_NULLS controla a nulidade padrão no banco de dados e a avaliação das comparações com valores nulos. Se ANSI_NULLS for ativado (o padrão), o operador IS NULL deverá ser usado nas expressões durante o teste de valores nulos. Por exemplo, a comparação a seguir sempre produzirá unknown quando ANSI_NULLS for ativado:  
  
```  
colname > NULL  
```  
  
 A comparação com uma variável contendo um valor nulo também produz unknown:  
  
```  
colname > @MyVariable  
```  
  
 Use o predicado IS NULL ou IS NOT NULL para testar um valor nulo. Isso pode adicionar complexidade à cláusula WHERE. Por exemplo, a coluna TerritoryID na tabela Customer do AdventureWorks permite valores nulos. Se uma instrução SELECT for destinada a testar valores nulos além de outros, ela deverá incluir um predicado IS NULL:  
  
```  
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 Se você desativar ANSI_NULLS no SQL Server, poderá criar expressões que usam o operador de igualdade para comparar com o valor nulo. No entanto, você não pode impedir que as diferentes conexões definam opções nulas para essa conexão. O uso de IS NULL para testar valores nulos sempre funciona, independentemente das configurações de ANSI_NULLS para uma conexão.  
  
 Não há suporte para a desativação de ANSI_NULLS em um `DataSet`, que sempre segue o padrão ANSI SQL-92 para manipular valores nulos no <xref:System.Data.SqlTypes>.  
  
## <a name="assigning-null-values"></a>Atribuindo valores nulos  
 Os valores nulos são especiais, e as semânticas de armazenamento e de atribuição diferem entre sistemas de tipo e sistemas de armazenamento. Um `Dataset` foi projetado para ser usado com diferentes sistemas de tipo e de armazenamento.  
  
 Esta seção descreve as semânticas nulas para atribuir valores nulos a <xref:System.Data.DataColumn> em um <xref:System.Data.DataRow> entre diferentes sistemas de tipo.  
  
 `DBNull.Value`  
 Esta atribuição é válida para uma `DataColumn` de qualquer tipo. Se o tipo implementar `INullable`, `DBNull.Value` será forçado no valor nulo fortemente tipado apropriado.  
  
 `SqlType.Null`  
 Todos os tipos de dados <xref:System.Data.SqlTypes> implementam `INullable`. Se o valor nulo fortemente tipado puder ser convertido no tipo de dados da coluna usando operadores de conversão implícitos, a atribuição deverá ser feita. Caso contrário, uma exceção de conversão inválida será lançada.  
  
 `null`  
 Se 'null' for um valor válido para o tipo de dado de dados `DataColumn`, ele será forçado no `DbNull.Value` ou `Null` associado ao tipo `INullable` (`SqlType.Null`)  
  
 `derivedUdt.Null`  
 Para colunas UDT, os valores nulos sempre são armazenados com base no tipo associado à `DataColumn`. Considere o caso de um UDT associado a uma `DataColumn` que não implementa `INullable` quando sua subclasse o faz. Nesse caso, se um valor nulo fortemente tipado associado à classe derivada for atribuído, ele será armazenado como um `DbNull.Value` não tipado, porque o armazenamento nulo é sempre consistente com o tipo de dados de DataColumn.  
  
> [!NOTE]
>  Não há suporte no momento para a estrutura `Nullable<T>` ou <xref:System.Nullable> no `DataSet`.  
  
### <a name="multiple-column-row-assignment"></a>Atribuição de várias colunas (linha)  
 `DataTable.Add`, `DataTable.LoadDataRow` ou outras APIs que aceitam um <xref:System.Data.DataRow.ItemArray%2A> que é mapeado para uma linha mapeiam 'null' para o valor padrão de DataColumn. Se um objeto na matriz contiver `DbNull.Value` ou seu equivalente fortemente tipado, as mesmas regras serão aplicadas conforme descrito acima.  
  
 Além disso, as seguintes regras se aplicam a uma instância de atribuições nulas de `DataRow.["columnName"]`:  
  
1.  O padrão *padrão* valor é `DbNull.Value` para todos exceto as colunas nulas fortemente tipadas onde é apropriado fortemente tipado valor nulo.  
  
2.  Os valores nulos nunca são gravados durante a serialização para arquivos XML (como em “xsi:nil").  
  
3.  Todos os valores não nulos, incluindo os valores padrão, sempre são gravados durante a serialização para XML. Esta é a semântica XSD/XML improvável, em que um valor nulo (xsi:nil) é explícito e o valor padrão é implícito (caso não esteja presente no XML, um analisador de validação poderá obtê-lo em um esquema XSD associado). O oposto é verdadeiro para `DataTable`: um valor nulo é implícito e o valor padrão é explícito.  
  
4.  Todos os valores de coluna ausentes para as linhas lidas na entrada XML recebem NULL. As linhas criadas por meio de <xref:System.Data.DataTable.NewRow%2A> ou de métodos similares recebem o valor padrão de DataColumn.  
  
5.  O método <xref:System.Data.DataRow.IsNull%2A> retorna `true` para `DbNull.Value` e `INullable.Null`.  
  
## <a name="assigning-null-values"></a>Atribuindo valores nulos  
 O valor padrão para qualquer instância de <xref:System.Data.SqlTypes> é nulo.  
  
 Os valores nulos em <xref:System.Data.SqlTypes> são específicos de tipo e não podem ser representado por um único valor, como `DbNull`. Use a propriedade `IsNull` para verificar valores nulos.  
  
 Os valores nulos podem ser atribuídos a <xref:System.Data.DataColumn> conforme mostrado no exemplo de código a seguir. Você pode atribuir diretamente valores nulos a variáveis `SqlTypes` sem disparar uma exceção.  
  
### <a name="example"></a>Exemplo  
 O exemplo de código a seguir cria <xref:System.Data.DataTable> com duas colunas definidas como <xref:System.Data.SqlTypes.SqlInt32> e <xref:System.Data.SqlTypes.SqlString>. O código adiciona uma linha de valores conhecidos, uma linha de valores nulos e faz a iteração por <xref:System.Data.DataTable>, atribuindo os valores às variáveis e exibindo a saída na janela do console.  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 Esse exemplo exibe os seguintes resultados:  
  
```  
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>Comparando valores nulos com SqlTypes e os tipos CLR  
 Durante a comparação dos valores nulos, é importante compreender a diferença entre a maneira como o método `Equals` avalia os valores nulos no <xref:System.Data.SqlTypes> e a maneira como ele funciona nos tipos CLR. Todos os métodos <xref:System.Data.SqlTypes>`Equals` usam a semântica de banco de dados para avaliar valores nulos: se qualquer um ou ambos os valores forem nulos, a comparação produzirá um valor nulo. Por outro lado, o uso do método CLR `Equals` em dois <xref:System.Data.SqlTypes> produzirá verdadeiro se ambos forem nulos. Isso refletirá a diferença entre o uso de um método de instância, como o método CLR `String.Equals`, e o uso do método estático/compartilhado, `SqlString.Equals`.  
  
 O exemplo a seguir mostra a diferença nos resultados entre os métodos `SqlString.Equals` e `String.Equals` quando cada um recebe um par de valores nulos e, em seguida, um par de cadeias de caracteres vazias.  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 O código produz a seguinte saída:  
  
```  
SqlString.Equals shared/static method:  
  Two nulls=Null  
  
String.Equals instance method:  
  Two nulls=True  
  
SqlString.Equals shared/static method:  
  Two empty strings=True  
  
String.Equals instance method:  
  Two empty strings=True   
```  
  
## <a name="see-also"></a>Consulte também  
 [SQL Server Data Types and ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md) (Tipos de dados do SQL Server e o ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
