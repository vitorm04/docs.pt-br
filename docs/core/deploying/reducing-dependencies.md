---
title: Reduzindo as dependências de pacote com o project.json
description: Reduza as dependências do pacote ao criar bibliotecas com base no project.json.
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.openlocfilehash: 6da7404415e8d485533fc1c9a619cb0706a26aca
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50040875"
---
# <a name="reducing-package-dependencies-with-projectjson"></a>Reduzindo as dependências de pacote com o project.json

Este artigo aborda o que você precisa saber sobre como reduzir suas dependências de pacote ao criar bibliotecas `project.json`. No final deste artigo, você aprenderá como compor sua biblioteca de forma que ela usa apenas as dependências necessárias. 

## <a name="why-its-important"></a>Por que isso é importante

O .NET Core é um produto composto por pacotes NuGet.  Um pacote essencial é o [metapacote .NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library), que é um pacote NuGet composto por outros pacotes.  Ele fornece o conjunto de pacotes que com certeza funcionam com diversas implementações .NET, como o .NET Framework, .NET Core e Xamarin/Mono.

No entanto, há uma boa chance de que a biblioteca não use todos os pacotes que ele contém.  Ao criar uma biblioteca e distribuí-la com o NuGet, é uma melhor prática “cortar” suas dependências para deixar apenas os pacotes que realmente serão usados.  Isso resulta em uma menor superfície geral de pacotes NuGet.

## <a name="how-to-do-it"></a>Como fazer isso

Atualmente, não há nenhum comando `dotnet` oficial para cortar as referências de pacote.  Em vez disso, você terá que fazê-lo manualmente.  O processo geral é semelhante ao seguinte:

1. Faça referência à `NETStandard.Library` versão `1.6.0` em uma seção `dependencies` de seu `project.json`.
2. Restaure pacotes com `dotnet restore` ([veja observação](#dotnet-restore-note)) por meio da linha de comando.
3. Inspecione o arquivo `project.lock.json` e localize a seção `NETSTandard.Library`.  Ele estará perto do início do arquivo.
4. Copie todos os pacotes listados em `dependencies`.
5. Remova a referência `.NETStandard.Library` e substitua-a pelos pacotes copiados.
6. Remova as referências aos pacotes que não são necessários.


Você pode descobrir quais pacotes não são necessários das seguintes maneiras:

1. Tentativa e erro.  Isso significa remover um pacote, restaurar, ver se sua biblioteca ainda é compilada e repetir esse processo.
2. Usar uma ferramenta como [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) ou [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector) para inspecionar as referências e ver o que seu código realmente está usando.  Você poderá então remover os pacotes que não correspondem aos tipos que você está usando.

## <a name="example"></a>Exemplo 

Imagine que você criou uma biblioteca que fornecia uma funcionalidade adicional para tipos de coleção genérica.  Uma biblioteca precisaria depender de pacotes como `System.Collections`, mas pode não de pacotes como `System.Net.Http`.  Dessa forma, seria bom cortar as dependências do pacote para reduzir até o que essa biblioteca realmente precisa.

Para cortar essa biblioteca, você deve começar com o arquivo `project.json` e adicionar uma referência ao `NETStandard.Library` versão `1.6.0`.

```json
{
    "version":"1.0.0",
    "dependencies":{
        "NETStandard.Library":"1.6.0"
    },
    "frameworks": {
        "netstandard1.0": {}
     }
}
```

Em seguida, restaure pacotes com `dotnet restore` ([veja observação](#dotnet-restore-note)), inspecione o arquivo `project.lock.json` e localize todos os pacotes restaurados para `NETSTandard.Library`.

Veja como a seção relevante no arquivo `project.lock.json` se parece ao redirecionar para `netstandard1.0`:

```json
"NETStandard.Library/1.6.0":{
    "type": "package",
    "dependencies": {
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    }
}
```

Em seguida, copie as referências do pacote para a seção `dependencies` do arquivo `project.json` da biblioteca, substituindo a referência `NETStandard.Library`:

```json
{
    "version":"1.0.0",
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
    }
}
```

Há um grande volume de pacotes, muitos dos quais certamente não são necessários para estender os tipos de coleção.  Você pode remover os pacotes manualmente ou usar uma ferramenta como [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) ou [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector/) para identificar quais pacotes seu código realmente usa.

Veja como um pacote cortado pareceria:

```json
{
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Linq": "4.1.0",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Runtime.Handles": "4.0.1",
        "System.Runtime.InteropServices": "4.1.0",
        "System.Runtime.InteropServices.RuntimeInformation": "4.0.0",
        "System.Threading.Tasks": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
     }
}
```

Agora, ele tem uma superfície menor do que se tivesse dependentes no metapacote `NETStandard.Library`.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]