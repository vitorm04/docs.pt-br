---
title: Cadeias de caracteres de conexão no ADO.NET
ms.date: 10/10/2018
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: bf053c7c26435bea5b2368c81c89b73e8949b74a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040145"
---
# <a name="connection-strings-in-adonet"></a>Cadeias de caracteres de conexão no ADO.NET

Uma cadeia de conexão contém informações de inicialização que são passadas como parâmetros de um provedor de dados para uma fonte de dados. O provedor de dados recebe a cadeia de conexão como o valor da propriedade <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType>. O provedor analisa a cadeia de conexão e garante que a sintaxe esteja correta e que as palavras-chave tenham suporte. Em seguida, o método <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> passa os parâmetros de conexão analisados para a fonte de dados. A fonte de dados executa uma validação adicional e estabelece uma conexão.

## <a name="connection-string-syntax"></a>Sintaxe da cadeia de conexão

Uma cadeia de conexão é uma lista delimitada por ponto-e-vírgula de pares de parâmetro de chave/valor:

```csharp
keyword1=value; keyword2=value;
```

As palavras-chave não diferenciam maiúsculas de minúsculas. Os valores, no entanto, podem diferenciar maiúsculas de minúsculas, dependendo da fonte de dados. As palavras-chave e os valores podem conter [caracteres de espaço em branco](https://en.wikipedia.org/wiki/Whitespace_character#Unicode). Espaços em branco à esquerda e à direita são ignorados em palavras-chave e valores sem aspas.

Se um valor contiver ponto e vírgula, [caracteres de controle Unicode](https://en.wikipedia.org/wiki/Unicode_control_characters)ou espaços em branco à esquerda ou à direita, ele deverá ser colocado entre aspas simples ou duplas. Por exemplo:

```csharp
Keyword=" whitespace  ";
Keyword='special;character';
```

O caractere delimitador pode não ocorrer dentro do valor que ele envolve. Portanto, um valor contendo aspas simples pode ser colocado entre aspas duplas, e vice-versa:

```csharp
Keyword='double"quotation;mark';
Keyword="single'quotation;mark";
```

Você também pode escapar do caractere delimitador usando dois juntos:

```csharp
Keyword="double""quotation";
Keyword='single''quotation';
```

As aspas em si, bem como o sinal de igual, não exigem saída, portanto, as seguintes cadeias de conexão são válidas:

```csharp
Keyword=no "escaping" 'required';
Keyword=a=b=c
```

Como cada valor é lido até o próximo ponto e vírgula ou o final da cadeia de caracteres, o valor no último exemplo é `a=b=c`e o ponto e vírgula final é opcional.

Todas as cadeias de conexão compartilham a mesma sintaxe básica descrita acima. O conjunto de palavras-chave reconhecidas depende do provedor, no entanto, e evoluiu ao longo dos anos de APIs anteriores, como *ODBC*. O provedor de dados *.NET Framework* para *SQL Server* (`SqlClient`) dá suporte a várias palavras-chave de APIs mais antigas, mas é geralmente mais flexível e aceita sinônimos para muitas das palavras-chave da cadeia de conexão comum.

Digitar erros pode causar erros. Por exemplo, `Integrated Security=true` é válido, mas `IntegratedSecurity=true` causa um erro.

Cadeias de conexão construídas manualmente em tempo de execução de entrada de usuário não validada são vulneráveis a ataques de injeção de cadeia de caracteres e ameaçam a segurança na fonte de dados. Para resolver esses problemas, o *ADO.NET* 2,0 introduziu [construtores de cadeia de conexão](connection-string-builders.md) para cada provedor de dados de *.NET Framework* . Esses construtores de cadeia de conexão expõem parâmetros como propriedades fortemente tipadas e possibilitam validar a cadeia de conexão antes que ela seja enviada para a fonte de dados.

## <a name="in-this-section"></a>Nesta seção

[Construtores de cadeia de conexão](connection-string-builders.md)\
Demonstra como usar as classes `ConnectionStringBuilder` para construir cadeias de conexão válidas em tempo de execução.

[Cadeias de conexão e arquivos de configuração](connection-strings-and-configuration-files.md)\
Demonstra como armazenar e recuperar cadeias de conexão em arquivos de configuração.

[Sintaxe de cadeia de conexão](connection-string-syntax.md)\
Descreve como configurar cadeias de conexão específicas do provedor para `SqlClient`, `OracleClient`, `OleDb` e `Odbc`.

[Protegendo as informações de conexão](protecting-connection-information.md)\
Demonstra técnicas para proteger informações usadas para se conectar a uma fonte de dados.

## <a name="see-also"></a>Consulte também

- [Conectando a uma fonte de dados](/cpp/data/odbc/connecting-to-a-data-source)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
