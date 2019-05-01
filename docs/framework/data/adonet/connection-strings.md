---
title: Cadeias de caracteres de conexão no ADO.NET
ms.date: 10/10/2018
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: 1197335f3ba2a09b6e7303d31bc32383d1fd3436
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032742"
---
# <a name="connection-strings-in-adonet"></a>Cadeias de caracteres de conexão no ADO.NET

Uma cadeia de conexão contém informações de inicialização que são passadas como parâmetros de um provedor de dados para uma fonte de dados. O provedor de dados recebe a cadeia de caracteres de conexão como o valor da <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> propriedade. O provedor analisa a cadeia de conexão e garante que a sintaxe está correta e que as palavras-chave têm suporte. Em seguida, a <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> método passa os parâmetros de conexão analisado para a fonte de dados. A fonte de dados executa a validação e estabelece uma conexão.

## <a name="connection-string-syntax"></a>Sintaxe de cadeia de caracteres de Conexão

Uma cadeia de caracteres de conexão é uma lista delimitada por ponto e vírgula de pares de chave/valor do parâmetro:

    keyword1=value; keyword2=value;

Palavras-chave não diferenciam maiusculas de minúsculas. No entanto, valores, podem ser diferencia maiusculas de minúsculas, dependendo da fonte de dados. Palavras-chave e valores podem conter [caracteres de espaço em branco](https://en.wikipedia.org/wiki/Whitespace_character#Unicode). Espaço em branco à esquerda e à direita será ignorado em palavras-chave e sem aspas valores.

Se um valor contém o ponto e vírgula [caracteres de controle Unicode](https://en.wikipedia.org/wiki/Unicode_control_characters), ou à esquerda ou à direita de espaço em branco, ela deve ser colocada entre aspas simples ou duplas. Por exemplo:

    Keyword=" whitespace  ";
    Keyword='special;character';

O caractere delimitador não pode ocorrer dentro do valor que ele inclui. Portanto, um valor que contém aspas simples pode ser colocado somente entre aspas duplas e vice-versa:

    Keyword='double"quotation;mark';
    Keyword="single'quotation;mark";

As aspas em si, bem como o sinal de igual, não exige o escape, portanto, as seguintes cadeias de caracteres de conexão são válidas:

    Keyword=no "escaping" 'required';
    Keyword=a=b=c

Uma vez que cada valor é lido até o próximo ponto e vírgula ou ao final da cadeia de caracteres, o valor no segundo exemplo é `a=b=c`, e o ponto e vírgula final é opcional.

Todas as cadeias de conexão compartilham a mesma sintaxe básica descrita acima. O conjunto de palavras-chave reconhecidas depende do provedor, no entanto e evoluiu ao longo dos anos desde as primeiras APIs, como *ODBC*. O *.NET Framework* provedor de dados para *SQL Server* (`SqlClient`) dá suporte a muitas palavras-chave das APIs mais antigas, mas é geralmente mais flexível e aceita sinônimos para muitos da cadeia de caracteres de conexão comum palavras-chave.

Erros de digitação podem causar erros. Por exemplo, `Integrated Security=true` é válido, mas `IntegratedSecurity=true` causa um erro.

Cadeias de caracteres de Conexão manualmente construídas em tempo de execução da entrada do usuário não validada são vulneráveis a ataques de injeção de cadeia de caracteres e colocar em risco a segurança na fonte de dados. Para resolver esses problemas *ADO.NET* 2.0 introduzida [construtores de cadeia de conexão](../../../../docs/framework/data/adonet/connection-string-builders.md) para cada *do .NET Framework* provedor de dados. Esses construtores de cadeia de conexão expõem parâmetros como propriedades fortemente tipadas e tornam possível validar a cadeia de caracteres de conexão antes de serem enviado à fonte de dados.

## <a name="in-this-section"></a>Nesta seção

[Construtores de cadeia de Conexão](../../../../docs/framework/data/adonet/connection-string-builders.md)\
Demonstra como usar as classes `ConnectionStringBuilder` para construir cadeias de conexão válidas em tempo de execução.

[Cadeias de caracteres de Conexão e arquivos de configuração](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)\
Demonstra como armazenar e recuperar cadeias de conexão em arquivos de configuração.

[Sintaxe de cadeia de caracteres de Conexão](../../../../docs/framework/data/adonet/connection-string-syntax.md)\
Descreve como configurar cadeias de conexão específicas do provedor para `SqlClient`, `OracleClient`, `OleDb` e `Odbc`.

[Proteção de informações de Conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md)\
Demonstra técnicas para proteger informações usadas para se conectar a uma fonte de dados.

## <a name="see-also"></a>Consulte também

- [Conectando a uma fonte de dados](/cpp/data/odbc/connecting-to-a-data-source)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
