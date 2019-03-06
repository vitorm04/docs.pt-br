---
title: Cadeias de caracteres de Conexão no ADO.NET Entity Framework
ms.date: 10/15/2018
ms.assetid: 78d516bc-c99f-4865-8ff1-d856bc1a01c0
ms.openlocfilehash: 55097e4977111c56cb06c590e305e31ed681fd31
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365029"
---
# <a name="connection-strings-in-the-adonet-entity-framework"></a>Cadeias de caracteres de Conexão no ADO.NET Entity Framework

Uma cadeia de conexão contém informações de inicialização que são passadas como parâmetros de um provedor de dados para uma fonte de dados. A sintaxe depende do provedor de dados, e a cadeia de conexão é analisada durante a tentativa de abrir uma conexão. As cadeias de conexão usadas por Entity Framework contêm informações usadas para conectar ao provedor de dados ADO.NET subjacente que dá suporte a Entity Framework. Elas também contêm informações sobre os arquivos de modelo e de mapeamento necessários.

A cadeia de conexão é usada pelo provedor EntityClient ao acessar metadados de modelo e de mapeamento e ao se conectar à fonte de dados. A cadeia de conexão pode ser acessada ou definida por meio da propriedade <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A> de <xref:System.Data.EntityClient.EntityConnection>. A classe <xref:System.Data.EntityClient.EntityConnectionStringBuilder> pode ser usada para construir ou acessar programaticamente parâmetros na cadeia de conexão. Para obter mais informações, confira [Como: Compilar uma cadeia de Conexão EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md).

O [ferramentas de modelo de dados de entidade](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) gerar uma cadeia de caracteres de conexão é armazenada no arquivo de configuração do aplicativo. O <xref:System.Data.Objects.ObjectContext> recupera essas informações de conexão automaticamente ao criar consultas de objeto. O <xref:System.Data.EntityClient.EntityConnection> usado por uma instância <xref:System.Data.Objects.ObjectContext> pode ser acessado a partir da propriedade <xref:System.Data.Objects.ObjectContext.Connection%2A>. Para obter mais informações, consulte [Gerenciando conexões e transações](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).

## <a name="connection-string-syntax"></a>Sintaxe da cadeia de conexão

Para saber mais sobre a sintaxe geral para cadeias de caracteres de conexão, consulte [sintaxe da cadeia de Conexão | Cadeias de caracteres de Conexão no ADO.NET](../connection-strings.md#connection-string-syntax).

## <a name="connection-string-parameters"></a>Parâmetros de cadeia de conexão

A tabela a seguir lista os nomes válidos para valores de palavra-chave na propriedade <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A>.

|Palavra-chave|Descrição|
|-------------|-----------------|
|`Provider`|Necessária quando a palavra-chave `Name` não é especificada. O nome do provedor, que é usado para recuperar o objeto <xref:System.Data.Common.DbProviderFactory> do provedor subjacente. Esse valor é constante.<br /><br /> Quando a palavra-chave `Name` não é incluída em uma cadeia de conexão de entidade, um valor não vazio para a palavra-chave `Provider` é necessário. Essa palavra-chave é mutuamente excludente com a palavra-chave `Name`.|
|`Provider Connection String`|Opcional. Especifica a cadeia de conexão específica ao provedor que é passada para a fonte de dados subjacente. Essa cadeia de caracteres de conexão contém pares de palavra-chave/valor válido para o provedor de dados. Uma palavra-chave `Provider Connection String` inválida produzirá um erro em tempo de execução ao ser avaliada pela fonte de dados.<br /><br /> Essa palavra-chave é mutuamente excludente com a palavra-chave `Name`.<br /><br /> Certifique-se de escape do valor de acordo com a sintaxe geral de [cadeias de caracteres de conexão ADO.NET](../../../../../docs/framework/data/adonet/connection-strings.md). Considere, por exemplo, a seguinte cadeia de conexão: `Server=serverName; User ID = userID`. Ela deverá ser substituída porque ela contém um ponto e vírgula. Uma vez que ele não contém aspas duplas, eles podem ser usados para escapar:<br /><br /> `Provider Connection String ="Server=serverName; User ID = userID";`|
|`Metadata`|Necessária quando a palavra-chave `Name` não é especificada. Uma lista de diretórios, arquivos e locais de recursos delimitados por pipe na qual procurar informações de metadados e mapeamento. A seguir está um exemplo:<br /><br /> `Metadata=`<br /><br /> `c:\model &#124; c:\model\sql\mapping.msl;`<br /><br /> Os espaços em branco em cada lado do separador de pipe são ignorados.<br /><br /> Essa palavra-chave é mutuamente excludente com a palavra-chave `Name`.|
|`Name`|O aplicativo pode, opcionalmente, especificar o nome da conexão em um arquivo de configuração do aplicativo que forneça os valores de cadeia de conexão de palavra-chave-valor necessários. Nesse caso, não é possível fornecê-los diretamente na cadeia de conexão. A palavra-chave `Name` não é permitida em um arquivo de configuração.<br /><br /> Quando a palavra-chave `Name` não é incluída na cadeia de conexão, um valor não vazio para a palavra-chave Provider é necessário.<br /><br /> Essa palavra-chave é mutuamente excludente com todos as outras palavras-chave de cadeia de conexão.|

A seguir está um exemplo de uma cadeia de conexão para o [modelo de vendas AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) armazenados no arquivo de configuração do aplicativo:

## <a name="model-and-mapping-file-locations"></a>Locais de arquivos de modelo e de mapeamento

O parâmetro `Metadata` contém uma lista de locais para que o provedor `EntityClient` pesquise arquivos de modelo e de mapeamento. Os arquivos de modelo e de mapeamento geralmente são implantados no mesmo diretório que o arquivo executável do aplicativo. Esses arquivos também podem ser implantados em um local específico ou ser incluídos como um recurso inserido no aplicativo.

Os recursos inseridos são especificados como a seguir:

```
Metadata=res://<assemblyFullName>/<resourceName>.
```

As seguintes opções estão disponíveis para definir o local de um recurso inserido:

|Opção|Descrição|
|-|-|
|`assemblyFullName`|O nome completo de um assembly com o recurso inserido. O nome inclui o nome simples, o nome da versão, a cultura com suporte e a chave pública, como a seguir:<br /><br /> `ResourceLib, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`<br /><br /> Os recursos podem ser inseridos em qualquer assembly que seja acessível pelo aplicativo.<br /><br /> Se você especificar um caractere curinga (\*) para `assemblyFullName`, o tempo de execução do Entity Framework pesquisará recursos nos locais a seguir, nesta ordem:<br /><br /> 1.  Assembly de chamada.<br />2.  Assemblies referenciados<br />3.  Assemblies no diretório bin de um aplicativo.<br /><br /> Se os arquivos não estiverem em um desses locais, será gerada uma exceção. **Observação:**  Quando você usar um curinga (*), o Entity Framework examinará em todos os assemblies se há recursos com o nome correto. Para melhorar o desempenho, especifique o nome do assembly, em vez do curinga.|
|`resourceName`|O nome do recurso incluído, como AdventureWorksModel.csdl. Os serviços de metadados só procuram arquivos ou recursos com uma das seguintes extensões: .csdl, .ssdl ou .msl. Se a palavra-chave `resourceName` não for especificada, todos os recursos de metadados serão carregados. Os recursos devem ter nomes exclusivos em um assembly. Se vários arquivos com o mesmo nome forem definidos em diferentes diretórios no assembly, a palavra-chave `resourceName` deverá incluir a estrutura de pastas antes do nome do recurso, por exemplo, FolderName.FileName.csdl.<br /><br /> `resourceName` não é necessária quando você especifica um curinga (*) para `assemblyFullName`.|

> [!NOTE]
> Para melhorar o desempenho, insira recursos no assembly de chamada, exceto em cenários não projetados para a Web, onde não há referências a arquivos subjacentes de mapeamento e de metadados no assembly de chamada.

O exemplo a seguir carrega todos os arquivos de modelo e de mapeamento no assembly de chamada, em assemblies referenciados e em outros assemblies no diretório bin de um aplicativo.

```
Metadata=res://*/
```

O exemplo a seguir carrega o arquivo model.csdl do assembly AdventureWorks e carrega os arquivos model.ssdl e model.msl do diretório padrão do aplicativo em execução.

```
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.csdl|model.ssdl|model.msl
```

O exemplo a seguir carrega os três recursos especificados do assembly específico.

```
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.csdl|
res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.ssdl|
res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.msl
```

O exemplo a seguir carrega todos os recursos inseridos com as extensões .csdl, .msl e .ssdl do assembly.

```
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/
```

O exemplo a seguir carrega todos os recursos no caminho do arquivo relativo adição "datadir\metadata\\" do local do assembly carregado.

```
Metadata=datadir\metadata\
```

O exemplo a seguir carrega todos os recursos no caminho de arquivo relativo do local do assembly carregado.

```
Metadata=.\
```

## <a name="support-for-the-124datadirectory124-substitution-string-and-the-web-application-root-operator-"></a>Suporte para o &#124;DataDirectory&#124; cadeia de caracteres de substituição e o aplicativo Web raiz de operador (~)

`DataDirectory` e o ~ operador são usados na <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A> como parte do `Metadata` e `Provider Connection String` palavras-chave. 
  <xref:System.Data.EntityClient.EntityConnection> encaminha `DataDirectory` e o operador ~ para <xref:System.Data.Metadata.Edm.MetadataWorkspace> e para o provedor de armazenamento, respectivamente.

|Termo|Descrição|
|----------|-----------------|
|`&#124;DataDirectory&#124;`|Resolve como um caminho relativo a arquivos de mapeamento e metadados. Este é o valor que é definido por meio do método `AppDomain.SetData("DataDirectory", objValue)`. O `DataDirectory` cadeia de caracteres de substituição deve ser cercada por caracteres de pipe e não pode haver nenhum espaço em branco entre seu nome e os caracteres de pipe. O nome `DataDirectory` não diferencia maiúsculas de minúsculas.<br /><br /> Se um diretório físico nomeado "DataDirectory" tiver de ser passado como um membro da lista de caminhos de metadados, adicione o espaço em branco para um ou ambos os lados do nome. Por exemplo: `Metadata="DataDirectory1 &#124; DataDirectory &#124; DataDirectory2"`. Um aplicativo ASP.NET resolve &#124;DataDirectory&#124; para a "\<raiz do aplicativo > / app_data" pasta.|
|~|Resolve como a raiz do aplicativo Web. O caractere ~ em uma posição à esquerda é sempre interpretado como o operador raiz do aplicativo Web (~), embora possa representar um subdiretório local válido. Para fazer referência a um subdiretório local, o usuário deve passar `./~` explicitamente.|

`DataDirectory` e o operador ~ devem ser especificados somente no início de um caminho; eles não são resolvidos em nenhuma outra posição. O Entity Framework tentará resolver `~/data`, mas tratará `/data/~` como um caminho físico.

Um caminho que começa com `DataDirectory` ou com o operador ~ não pode ser resolvido como um caminho físico fora da ramificação de `DataDirectory` e do operador ~. Por exemplo, os seguintes caminhos serão resolvidos: `~`, `~/data`, `~/bin/Model/SqlServer`. Os seguintes caminhos não serão resolvidos: `~/..`, `~/../other`.

`DataDirectory` e o ~ operador pode ser estendido para incluir subdiretórios, da seguinte maneira: `|DataDirectory|\Model`, `~/bin/Model`

A resolução da cadeia de caracteres de substituição `DataDirectory` e do operador ~ é não recursiva. Por exemplo, quando `DataDirectory` incluir o caractere `~`, será gerada uma exceção. Isso evita uma recursão infinita.

## <a name="see-also"></a>Consulte também

- [Trabalhando com Provedores de Dados](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)
- [Considerações de implantação](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)
- [Gerenciando conexões e transações](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))
- [Cadeia de Conexão](../../../../../docs/framework/data/adonet/connection-strings.md)
