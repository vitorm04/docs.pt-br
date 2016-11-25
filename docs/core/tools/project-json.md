---
title: "Referência do project.json"
description: "Referência do project.json"
keywords: .NET, .NET Core, project.json
author: aL3891
ms.author: mairaw
manager: wpickett
ms.date: 09/30/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 3aef32bd-ee2a-4e24-80f8-a2b615e0336d
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: ce3dbad938c01fd0f9d79cefb29884be986b8e1f

---

# <a name="projectjson-reference"></a>Referência do project.json

O arquivo project.json é usado em projetos .NET Core para definir metadados do projeto, informações de compilação e dependências. Nesse tópico de referência, você verá a lista de todas as propriedades que podem ser definidas no arquivo project.json.

> [!NOTE]
> As ferramentas do .NET Core serão movidas do project.json para projetos baseados em MSBuild em uma versão futura. A recomendação é continuar usando esses arquivos project.json para novos projetos .NET Core, visto que haverá um caminho para converter o projeto para MSBuild quando a ferramenta for lançada.
>
> Para obter mais informações, consulte a postagem [Mudanças do project.json](https://blogs.msdn.microsoft.com/dotnet/2016/05/23/changes-to-project-json/) no blog do .NET e o tópico [Usando o MSBuild para compilar projetos .NET Core](../tutorials/target-dotnetcore-with-msbuild.md).

## <a name="overview"></a>Visão Geral

```
{
    "name": String,
    "version": String,
    "description": String,
    "copyright": String,
    "title": String,
    "entryPoint": String,
    "testRunner": String,
    "authors": String[],
    "language": String,
    "embedInteropTypes": Boolean,
    "preprocess": String or String[],
    "shared": String or String[],
    "dependencies": Object {
        version: String,
        type: String,
        target: String,
        include: String,
        exclude: String,
        suppressParent: String
    },
    "tools": Object,
    "scripts": Object,
    "buildOptions": Object {
        "define": String[],
        "nowarn": String[],
        "additionalArguments": String[],
        "warningsAsErrors": Boolean,
        "allowUnsafe": Boolean,
        "emitEntryPoint": Boolean,
        "optimize": Boolean,
        "platform": String,
        "languageVersion": String,
        "keyFile": String,
        "delaySign": Boolean,
        "publicSign": Boolean,
        "debugType": String,
        "xmlDoc": Boolean,
        "preserveCompilationContext": Boolean,
        "outputName": String,
        "compilerName": String,
        "compile": Object {
            "include": String or String[],
            "exclude": String or String[],
            "includeFiles": String or String[],
            "excludeFiles": String or String[],
            "builtIns": Object,
            "mappings": Object
        },
        "embed": Object {
            "include": String or String[],
            "exclude": String or String[],
            "includeFiles": String or String[],
            "excludeFiles": String or String[],
            "builtIns": Object,
            "mappings": Object
        },
        "copyToOutput": Object {
            "include": String or String[],
            "exclude": String or String[],
            "includeFiles": String or String[],
            "excludeFiles": String or String[],
            "builtIns": Object,
            "mappings": Object
        }
    },
    "publishOptions": Object {
        "include": String or String[],
        "exclude": String or String[],
        "includeFiles": String or String[],
        "excludeFiles": String or String[],
        "builtIns": Object,
        "mappings": Object
    },
    "runtimeOptions": Object {
        "configProperties": Object {
            "System.GC.Server": Boolean,
            "System.GC.Concurrent": Boolean,
            "System.GC.RetainVM": Boolean,
            "System.Threading.ThreadPool.MinThreads": Integer,
            "System.Threading.ThreadPool.MaxThreads": Integer
        },
        "framework": Object {
            "name": String,
            "version": String,
        },
        "applyPatches": Boolean
    },
    "packOptions": Object {
        "summary": String,
        "tags": String[],
        "owners": String[],
        "releaseNotes": String,
        "iconUrl": String,
        "projectUrl": String,
        "licenseUrl": String,
        "requireLicenseAcceptance": Boolean,
        "repository": Object {
            "type": String,
            "url": String
        },
        "files": Object {
            "include": String or String[],
            "exclude": String or String[],
            "includeFiles": String or String[],
            "excludeFiles": String or String[],
            "builtIns": Object,
            "mappings": Object
        }
    },
    "analyzerOptions": Object {
        "languageId": String
    },
    "configurations": Object,
    "frameworks": Object {
        "dependencies": Object {
            version: String,
            type: String,
            target: String,
            include: String,
            exclude: String,
            suppressParent: String
        },        
        "frameworkAssemblies": Object,
        "wrappedProject": String,
        "bin": Object {
            assembly: String
        }
    },
    "runtimes": Object,
    "userSecretsId": String
}
```

## <a name="name"></a>name
Tipo: String

O nome do projeto, usado para o nome do assembly, bem como o nome do pacote. O nome da pasta de nível superior será usado se esta propriedade não for especificada.

Por exemplo:

```json
{
    "name": "MyLibrary"
}
```

## <a name="version"></a>version
Tipo: String

A versão [Semver](http://semver.org/spec/v1.0.0.html) do projeto, que também é usada para o pacote NuGet.

Por exemplo:

```json
{
    "version": "1.0.0-*"
}
```

## <a name="description"></a>descrição
Tipo: String

Uma descrição mais longa do projeto. Usada nas propriedades de assembly.

Por exemplo:

```json
{
    "description": "This is my library and it's really great!"
}
```

## <a name="copyright"></a>direitos autorais
Tipo: String

As informações de direitos autorais do projeto. Usada nas propriedades de assembly.

Por exemplo:

```json
{
    "copyright": "Fabrikam 2016"
}
```

## <a name="title"></a>título
Tipo: String

O nome amigável do projeto, que pode conter espaços e caracteres especiais não permitidos ao usar a propriedade `name`. Usada nas propriedades de assembly.

Por exemplo:

```json
{
    "title": "My Library"
}
```

## <a name="entrypoint"></a>entryPoint
Tipo: String

O método de ponto de entrada do projeto. `Main` por padrão.

Por exemplo:

```json
{
    "entryPoint": "ADifferentMethod"
}
```
    
## <a name="testrunner"></a>testRunner
Tipo: String

O nome do executor de teste, como [NUnit](http://nunit.org/) ou [xUnit](http://xunit.github.io/), a ser usado neste projeto. Definir isso marca o projeto como um projeto de teste.

Por exemplo:

```json
{
    "testRunner": "NUnit"
}
```

## <a name="authors"></a>authors
Digite: String[]

Uma matriz de cadeias de caracteres com os nomes de autores do projeto.

Por exemplo:

```json
{
    "authors": ["Anne", "Bob"]
}
```

## <a name="language"></a>linguagem
Tipo: String

O idioma (humano) do projeto. Corresponde ao argumento de compilador de “neutro de idioma”.

Por exemplo:

```json
{
    "language": "en-US"
}
```

## <a name="embedinteroptypes"></a>embedInteropTypes
Tipo: Boolean

`true` para inserir tipos de interoperabilidade COM no assembly; caso contrário, `false`. 

Por exemplo:

```json
{
    "embedInteropTypes": true
}
```

## <a name="preprocess"></a>preprocess
Tipo: String ou String[] com um padrão de recurso de curinga

Especifica quais arquivos estão incluídos no pré-processamento.

Por exemplo:

```json
{
    "preprocess": "compiler/preprocess/**/*.cs"
}
```

## <a name="shared"></a>shared
Tipo: String ou String[] com um padrão de recurso de curinga

Especifica quais arquivos são compartilhados, o que é usado para exportação de biblioteca.

Por exemplo:

```json
{
    "shared": "shared/**/*.cs"
}
```

## <a name="dependencies"></a>dependências
Tipo: Object

Um objeto que define as dependências do pacote do projeto, cada chave desse objeto é o nome de um pacote e cada valor contém informações de controle de versão.
Para obter mais informações, consulte o artigo [Resolução de dependências](https://docs.nuget.org/ndocs/consume-packages/dependency-resolution#dependency-resolution-in-nuget-3-x) no site de documentação do NuGet.

Por exemplo:

```json
    "dependencies": {
        "System.Reflection.Metadata": "1.3.0",
        "Microsoft.Extensions.JsonParser.Sources": {
          "type": "build",
          "version": "1.0.0-rc2-20221"
        },
        "Microsoft.Extensions.HashCodeCombiner.Sources": {
          "type": "build",
          "version": "1.1.0-alpha1-21456"
        },
        "Microsoft.Extensions.DependencyModel": "1.0.0-*"
    }
```

### <a name="version"></a>version
Tipo: String

Especifica a versão ou o intervalo de versões da dependência. Use o curinga \* para especificar uma [versão de dependência flutuante](https://docs.nuget.org/ndocs/consume-packages/dependency-resolution#floating-versions).

Por exemplo:

```json
"dependencies": { 
    "Newtonsoft.Json": { 
        "version": "9.0.1" 
    }
}
```

### <a name="type"></a>tipo
Tipo: String

Especifica o tipo da dependência. Pode ser um dos seguintes valores: `default`, `build` ou `platform`. O valor padrão é `default`.

`build` é conhecido como uma dependência de desenvolvimento e só é usada no tempo de build. Isso significa que o pacote não deve ser publicado ou adicionado como uma dependência no arquivo de saída `.nupkg`. Tem o mesmo efeito que configurar [supressParent](#supressparent) como `all`.

`platform` referencia o SDK compartilhado. Para obter mais informações, consulte a seção em “Implantando uma implantação dependente de estrutura com dependências de terceiros” no tópico [Implantação de .NET Core Application](../deploying/index.md).

Por exemplo:

```json
 "dependencies": {
   "Microsoft.NETCore.App": {
     "type": "platform",
     "version": "1.0.0"
   }
 }
```

### <a name="target"></a>destino
Tipo: String

Restringe a dependência para corresponder apenas a um `project` ou um `package`.

### <a name="include"></a>include
Tipo: String

Inclui as partes de pacotes de dependência. Pode usar um ou mais dos seguintes sinalizadores: `all`, `runtime`, `compile`, `build`, `contentFiles`, `native`, `analyzers` ou `none`.
Diversos sinalizadores são definidos por uma lista delimitada por vírgulas.
Para obter mais informações, consulte a especificação [Gerenciamento de ativos de pacote de dependência](https://github.com/NuGet/Home/wiki/%5BSpec%5D-Managing-dependency-package-assets) no repositório do NuGet.

Por exemplo:

```json
{
  "dependencies": {
    "packageA": {
      "version": "1.0.0",
      "include": "runtime"
    }
  }
}
```

### <a name="exclude"></a>exclude
Tipo: String

Exclui as partes de pacotes de dependência. Pode ser um ou mais dos seguintes sinalizadores: `all`, `runtime`, `compile`, `build`, `contentFiles`, `native`, `analyzers` ou `none`.
Diversos sinalizadores são definidos por uma lista delimitada por vírgulas.
Para obter mais informações, consulte a especificação [Gerenciamento de ativos de pacote de dependência](https://github.com/NuGet/Home/wiki/%5BSpec%5D-Managing-dependency-package-assets) no repositório do NuGet.

Por exemplo:

```json
{
  "dependencies": {
    "packageA": {
      "version": "1.0.0",
      "exclude": "contentFiles"
    }
  }
}
```

### <a name="supressparent"></a>supressParent
Tipo: String

Define exclusões adicionais para os consumidores do projeto. Pode ser um dos seguintes sinalizadores: `all`, `runtime`, `compile`, `build`, `contentFiles`, `native`, `analyzers` ou `none`.
Para obter mais informações, consulte a especificação [Gerenciamento de ativos de pacote de dependência](https://github.com/NuGet/Home/wiki/%5BSpec%5D-Managing-dependency-package-assets) no repositório do NuGet.

```json
{
  "dependencies": {
    "packageA": {
      "version": "1.0.0",
      "suppressParent": "compile"
    }
  }
}
```

## <a name="tools"></a>ferramentas
Tipo: Object

Um objeto que define as dependências de pacotes que são usadas como ferramentas para o projeto atual, não como referências. Os pacotes definidos aqui estão disponíveis em scripts que são executados durante o processo de build, mas não estão acessíveis para o código no próprio projeto. Por exemplo, a ferramentas podem incluir geradores de código ou ferramentas pós-build que executam tarefas relacionadas ao empacotamento.

Por exemplo:

```json
{
    "tools": {
    "MyObfuscator": "1.2.4"
    }
}
```

## <a name="scripts"></a>scripts
Tipo: Object

Um objeto que define que os scripts são executados durante o processo de build. Cada chave nesse objeto identifica onde executar o script no build. Cada valor é uma cadeia de caracteres com o script a ser executado ou uma matriz de cadeias de caracteres que contém scripts que serão executados em ordem.
Os eventos com suporte são:
* precompile
* postcompile
* prepublish
* postpublish

Por exemplo:

```json
{
    "scripts": {
        "precompile": "generateCode.cmd",
        "postcompile": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
    }
}
```

## <a name="buildoptions"></a>buildOptions
Tipo: Object

Um objeto cujas propriedades controlam vários aspectos da compilação. As propriedades válidas estão listadas abaixo. Também pode ser especificado por estrutura de destino, conforme descrito na [seção de estruturas](#frameworks).

Por exemplo:

```json
    "buildOptions": {
      "allowUnsafe": true,
      "emitEntryPoint": true
    }
```

### <a name="define"></a>define
Digite: String[]

Uma lista de definições como “DEBUG” ou “TRACE”, o que pode ser usado na compilação condicional no código.

Por exemplo:

```json
{
    "buildOptions": {
        "define": ["TEST", "OTHERCONDITION"]
    }
}
```

### <a name="nowarn"></a>nowarn
Digite: String[]

Uma lista de avisos a serem ignorados.

Por exemplo:

```json
{
    "buildOptions": {
        "nowarn": ["CS0168", "CS0219"]
    }
}
```

Isso ignora os avisos `The variable 'var' is assigned but its value is never used` e `The variable 'var' is assigned but its value is never used`

### <a name="additionalarguments"></a>additionalArguments
Digite: String[]

Uma lista de argumentos extras que serão passados para o compilador.

Por exemplo:

```json
{
    "buildOptions": {
        "additionalArguments": ["/parallel", "/nostdlib"]
    }
}
```

### <a name="warningsaserrors"></a>warningsAsErrors
Tipo: Boolean

`true` para tratar avisos como erros; caso contrário, `false`. O padrão é `false`.

Por exemplo:

```json
{
    "buildOptions": {
        "warningsAsErrors": true
    }
}
```

### <a name="allowunsafe"></a>allowUnsafe
Tipo: Boolean

`true` para permitir código não seguro neste projeto; caso contrário, `false`. O padrão é `false`.

Por exemplo:

```json
{
    "buildOptions": {
        "allowUnsafe": true
    }
}
```

### <a name="emitentrypoint"></a>emitEntryPoint
Tipo: Boolean

`true` para criar um executável; `false` para produzir uma biblioteca. O padrão é `false`.

Por exemplo:

```json
{
    "buildOptions": {
        "emitEntryPoint": true
    }
}
```

### <a name="optimize"></a>optimize
Tipo: Boolean

`true` para habilitar o compilador para otimizar o código neste projeto; caso contrário, `false`. O padrão é `false`.

Por exemplo:

```json
{
    "buildOptions": {
        "optimize": true
    }
}
```

### <a name="platform"></a>platform
Tipo: String

O nome da plataforma de destino, tal como AnyCpu, x86 ou x64.

Por exemplo:

```json
{
    "buildOptions": {
        "platform": "x64"
    }
}
```

### <a name="languageversion"></a>languageVersion
Tipo: String

A versão da linguagem usada pelo compilador: ISO-1, ISO-2, 3, 4, 5, 6 ou Default.

Por exemplo:

```json
{
    "buildOptions": {
        "languageVersion": "5"
    }
}
```

### <a name="keyfile"></a>keyFile
Tipo: String

O caminho para o arquivo da chave usado para assinar esse assembly.

Por exemplo:

```json
{
    "buildOptions": {
        "keyFile": "../keyfile.snk"
    }
}
```

### <a name="delaysign"></a>delaySign
Tipo: Boolean

`true` para atrasar a assinatura; caso contrário, `false`. O padrão é `false`.

Por exemplo:

```json
{
    "buildOptions": {
        "delaySign": true
    }
}
```

### <a name="publicsign"></a>publicSign
Tipo: Boolean

`true` para habilitar a assinatura do assembly resultante; caso contrário, `false`. O padrão é `false`.

Por exemplo:

```json
{
    "buildOptions": {
        "publicSign": true
    }
}
```

### <a name="debugtype"></a>debugType
Tipo: String

Indica o tipo do arquivo de símbolo (arquivo PDB) a ser gerado. As opções são “portátil” (para projetos .NET Core) ou “completo” (os arquivos PDB tradicionais exclusivos do Windows).

Por exemplo:

```json
{
    "buildOptions": {
        "debugType": "portable"
    }
}
```

### <a name="xmldoc"></a>xmlDoc
Tipo: Boolean

`true` para gerar a documentação XML de comentários de barra tripla no código-fonte; caso contrário, `false`. O padrão é `false`.

Por exemplo:

```json
{
    "buildOptions": {
        "xmlDoc": true
    }
}
```

### <a name="preservecompilationcontext"></a>preserveCompilationContext
Tipo: Boolean

`true` para preservar os assemblies de referência e outros dados de contexto para permitir a compilação de tempo de execução; caso contrário, `false`. O padrão é `false`.

Por exemplo:

```json
{
    "buildOptions": {
        "preserveCompilationContext": true
    }
}
```

### <a name="outputname"></a>outputName
Tipo: String

Alterar o nome do arquivo de saída. 

Por exemplo:

```json
{
    "buildOptions": {
        "outputName": "MyApp"
    }
}
```

### <a name="compilername"></a>compilerName
Tipo: String

O nome do compilador usado para este projeto. `csc` por padrão. Atualmente, há suporte para `csc` (o compilador C#) ou `fsc` (o compilador F#).
 
Por exemplo:

```json
{
    "compilerName": "fsc"
}
```
    
### <a name="compile"></a>compilar
Tipo: Object

Um objeto que contém as propriedades de configuração de compilação.

#### <a name="include"></a>include
Tipo: String ou String[] com um padrão de recurso de curinga.

Especifica quais arquivos serão incluídos o build. A raiz dos padrões está na pasta do projeto. Assume o padrão de Nenhum.

Por exemplo:

```json
{
    "include":["wwwroot", "Views"]
}
```

#### <a name="exclude"></a>exclude
Tipo: String ou String[] com um padrão de recurso de curinga.

Especifica quais arquivos serão excluídos do build. Os padrões de exclusão têm prioridade maior do que os de inclusão, por isso um arquivo localizado em ambos será excluído. A raiz dos padrões está na pasta do projeto. Assume o padrão de Nenhum.

Por exemplo:

```json
{
    "exclude": ["bin/**", "obj/**"]
}
```

#### <a name="includefiles"></a>includeFiles

Tipo: String ou String[] com um padrão de recurso de curinga.

Uma lista de caminhos de arquivos a serem incluídos. A raiz dos caminhos está na pasta do projeto. Essa lista tem uma prioridade maior que os padrões de recurso de curinga de inclusão e exclusão, por isso um arquivo listados aqui e no padrão de recurso de curinga de exclusão ainda será incluído. Assume o padrão de Nenhum.

Por exemplo:

```json
{
    "includeFiles": []
}
```

#### <a name="excludefiles"></a>excludeFiles

Tipo: String ou String[] com um padrão de recurso de curinga.

Uma lista de caminhos de arquivos a serem excluídos. A raiz dos caminhos está na pasta do projeto. Essa lista tem uma prioridade maior que os padrões de recurso de curinga e caminhos de inclusão, por isso um arquivo encontrado em todos eles será excluído. Assume o padrão de Nenhum.

Por exemplo:

```json
{
    "excludeFiles":[],
}
```

#### <a name="builtins"></a>builtIns

Tipo: Object

O padrão fornecido pelo sistema. Ele pode ter padrões de recurso de curinga `include` e `exclude`, os quais são mesclados com os respectivos valores das propriedades `include` e `exclude`.

Por exemplo:

```json
{
    "builtIns":{}
}
```

#### <a name="mappings"></a>mapeamentos
Tipo: Object

Chaves para o objeto representam caminhos de destino no layout de saída.

Os valores são uma cadeia de caracteres ou um objeto que representa o caminho de origem dos arquivos a serem incluídos.  A representação do objeto pode ter suas próprias seções `include`, `exclude`, `includeFiles` e `excludeFiles`.

Exemplo de cadeia de caracteres:

```json
{
    "mappings": {
        "dest/path": "./src/path"
    }
}
```

Exemplo de objeto:

```json
{
    "mappings": {
        "dest/path":{
            "include":"./src/path"
        }
    }
}
```

### <a name="embed"></a>embed
Tipo: Object

Um objeto que contém as propriedades de configuração de compilação.

#### <a name="include"></a>include
Tipo: String ou String[] com um padrão de recurso de curinga.

```json
{
    "include":["wwwroot", "Views"]
}
```

#### <a name="exclude"></a>exclude
Tipo: String ou String[] com um padrão de recurso de curinga.

Especifica quais arquivos serão excluídos do build.

Por exemplo:

```json
{
    "exclude": ["bin/**", "obj/**"]
}
```

#### <a name="includefiles"></a>includeFiles

Tipo: String ou String[] com um padrão de recurso de curinga.

```json
{
    "includeFiles":[],
}
```

#### <a name="excludefiles"></a>excludeFiles

Tipo: String ou String[] com um padrão de recurso de curinga.

```json
{
    "excludeFiles":[],
}
```

#### <a name="builtins"></a>builtIns
Tipo: Object

```json
{
    "builtIns":{}
}
```

#### <a name="mappings"></a>mapeamentos
Tipo: Object

Chaves para o objeto representam caminhos de destino no layout de saída.

Os valores são uma cadeia de caracteres ou um objeto que representa o caminho de origem dos arquivos a serem incluídos.  A representação do objeto pode ter suas próprias seções `include`, `exclude`, `includeFiles` e `excludeFiles`.

Exemplo de cadeia de caracteres:

```json
{
    "mappings": {
        "dest/path": "./src/path"
    }
}
```

Exemplo de objeto:

```json
{
    "mappings": {
        "dest/path":{
            "include":"./src/path"
        }
    }
}
```

### <a name="copytooutput"></a>copyToOutput
Tipo: Object

Um objeto que contém as propriedades de configuração de compilação.

#### <a name="include"></a>include
Tipo: String ou String[] com um padrão de recurso de curinga.

```json
{
    "include":["wwwroot", "Views"]
}
```

#### <a name="exclude"></a>exclude
Tipo: String ou String[] com um padrão de recurso de curinga.

Especifica quais arquivos serão excluídos do build.

Por exemplo:

```json
{
    "exclude": ["bin/**", "obj/**"]
}
```

#### <a name="includefiles"></a>includeFiles

Tipo: String ou String[] com um padrão de recurso de curinga.

```json
{
    "includeFiles":[],
}
```

#### <a name="excludefiles"></a>excludeFiles

Tipo: String ou String[] com um padrão de recurso de curinga.

```json
{
    "excludeFiles":[],
}
```

#### <a name="builtins"></a>builtIns
Tipo: Object

```json
{
    "builtIns":{}
}
```

#### <a name="mappings"></a>mapeamentos
Tipo: Object

Chaves para o objeto representam caminhos de destino no layout de saída.

Os valores são uma cadeia de caracteres ou um objeto que representa o caminho de origem dos arquivos a serem incluídos.  A representação do objeto pode ter suas próprias seções `include`, `exclude`, `includeFiles` e `excludeFiles`.

Exemplo de cadeia de caracteres:

```json
{
    "mappings": {
        "dest/path": "./src/path"
    }
}
```

Exemplo de objeto:

```json
{
    "mappings": {
        "dest/path":{
            "include":"./src/path"
        }
    }
}
```

## <a name="publishoptions"></a>publishOptions
Tipo: Object

Um objeto que contém as propriedades de configuração de compilação.

### <a name="include"></a>include
Tipo: String ou String[] com um padrão de recurso de curinga.

```json
{
    "include":["wwwroot", "Views"]
}
```

### <a name="exclude"></a>exclude
Tipo: String ou String[] com um padrão de recurso de curinga.

Especifica quais arquivos serão excluídos do build.

Por exemplo:

```json
{
    "exclude": ["bin/**", "obj/**"]
}
```

### <a name="includefiles"></a>includeFiles

Tipo: String ou String[] com um padrão de recurso de curinga.

```json
{
    "includeFiles":[],
}
```

### <a name="excludefiles"></a>excludeFiles

Tipo: String ou String[] com um padrão de recurso de curinga.

```json
{
    "excludeFiles":[],
}
```

### <a name="builtins"></a>builtIns
Tipo: Object

```json
{
    "builtIns":{}
}
```

### <a name="mappings"></a>mapeamentos
Tipo: Object

Chaves para o objeto representam caminhos de destino no layout de saída.

Os valores são uma cadeia de caracteres ou um objeto que representa o caminho de origem dos arquivos a serem incluídos.  A representação do objeto pode ter suas próprias seções `include`, `exclude`, `includeFiles` e `excludeFiles`.

Exemplo de cadeia de caracteres:

```json
{
    "mappings": {
        "dest/file": "./src/file",
        "dest/folder/": "./src/folder/**/*"
    }
}
```

Exemplo de objeto:

```json
{
    "mappings": {
        "dest/file":{
            "include":"./src/file"
        },
        "dest/folder/":{
            "include":"./src/folder/**/*"
        }
    }
}
```

## <a name="runtimeoptions"></a>runtimeOptions
Tipo: Object

Especifica os parâmetros a serem fornecidos no tempo de execução durante a inicialização.

### <a name="configproperties"></a>configProperties
Tipo: Object

Contém as propriedades de configuração para definir o tempo de execução e a estrutura.

#### <a name="systemgcserver"></a>System.GC.Server
Tipo: Boolean

`true` para habilitar a coleta de lixo do servidor; caso contrário, `false`. O padrão é `false`.

Por exemplo:

```json
{
    "runtimeOptions": {
        "configProperties": {
            "System.GC.Server": true
        }
    }
}
```

#### <a name="systemgcconcurrent"></a>System.GC.Concurrent
Tipo: Boolean

`true` para habilitar a coleta de lixo simultânea; caso contrário, `false`. O padrão é `false`.

Por exemplo:

```json
{
    "runtimeOptions": {
        "configProperties": {
            "System.GC.Concurrent": true
        }
    }
}
```

#### <a name="systemgcretainvm"></a>System.GC.RetainVM
Tipo: Boolean

`true` para colocar os segmentos que devem ser excluídos em uma lista de espera para uso futuro, em vez de liberá-los para o sistema operacional (SO); caso contrário, `false`.
O padrão é `false`.

Por exemplo:

```json
{
    "runtimeOptions": {
        "configProperties": {
            "System.GC.RetainVM": true
        }
    }
}
```

#### <a name="systemthreadingthreadpoolminthreads"></a>System.Threading.ThreadPool.MinThreads
Tipo: Integer

Substitui o número de threads mínimo para o pool de trabalho ThreadPool.

```json
{
    "runtimeOptions": {
        "configProperties": {
            "System.Threading.ThreadPool.MinThreads": 4
        }
    }
}
```

#### <a name="systemthreadingthreadpoolmaxthreads"></a>System.Threading.ThreadPool.MaxThreads
Tipo: Integer

Substitui o número de threads máximo para o pool de trabalho ThreadPool.

```json
{
    "runtimeOptions": {
        "configProperties": {
            "System.Threading.ThreadPool.MaxThreads": 25
        }
    }
}
```

### <a name="framework"></a>estrutura
Tipo: Object

Contém propriedades de estrutura compartilhada para ser usada ao ativar o aplicativo. A presença desta seção indica que o aplicativo é um aplicativo portátil projetado para usar uma estrutura redistribuível compartilhada.

#### <a name="name"></a>name
Tipo: String

Nome da estrutura compartilhada.

```json
{
    "runtimeOptions": {
        "framework": {
            "name": "Microsoft.DotNetCore"
        }
    }
}
```

#### <a name="version"></a>version
Tipo: String

Versão da estrutura compartilhada.

```json
{
    "runtimeOptions": {
        "framework": {
            "version": "1.0.1"
        }
    }
}
```

### <a name="applypatches"></a>applyPatches
Tipo: Boolean

`true` para usar a estrutura da mesma versão ou de uma versão posterior que difere somente no campo `SemVer` do patch. `false` para o host usar somente a versão exata da estrutura. O padrão é `true`.

```json
{
    "runtimeOptions": {
        "applyPatches": false
    }
}
```

## <a name="packoptions"></a>packOptions
Tipo: Object

Define opções referentes ao empacotamento da saída do projeto em um pacote NuGet.

### <a name="summary"></a>resumo
Tipo: String

Uma breve descrição do projeto.

Por exemplo:

```json
{
    "packOptions": {
        "summary": "This is my library."
    }
}
```

### <a name="tags"></a>marcações
Digite: String[]

Uma matriz de cadeias de caracteres com marcas para o projeto, usada para pesquisar no NuGet.

Por exemplo:

```json
{
    "packOptions": {
        "tags": ["hyperscale", "cats"]
    }
}
```

### <a name="owners"></a>owners
Digite: String[]

Uma matriz de cadeias de caracteres com os nomes dos proprietários do projeto.

Por exemplo:

```json
{
    "packOptions": {
        "owners": ["Fabrikam", "Microsoft"]
    }
}
```

### <a name="releasenotes"></a>releaseNotes
Tipo: String

Notas de versão para o projeto.

Por exemplo:

```json
{
    "packOptions": {
        "releaseNotes": "Initial version, implemented flimflams."
    }
}
```

### <a name="iconurl"></a>iconUrl
Tipo: String

A URL de um ícone que será usada em vários lugares, tal como o explorador de pacotes.

Por exemplo:

```json
{
    "packOptions": {
        "iconUrl": "http://www.mylibrary.gov/favicon.ico"
    }
}
```

### <a name="projecturl"></a>projectUrl
Tipo: String

A URL da home page do projeto.

Por exemplo:

```json
{
    "packOptions": {
        "projectUrl": "http://www.mylibrary.gov"
    }
}
```

### <a name="licenseurl"></a>licenseUrl
Tipo: String

A URL da licença que o projeto utiliza.

Por exemplo:

```json
{
    "packOptions": {
        "licenseUrl": "http://www.mylibrary.gov/licence"
    }
}
```

### <a name="requirelicenseacceptance"></a>requireLicenseAcceptance
Tipo: Boolean

`true` para mostrar um prompt para aceitar a licença do pacote ao instalá-lo; caso contrário, `false`. Usado apenas para pacotes NuGet, ignorados em outros usos. O padrão é `false`.

Por exemplo:

```json
{
    "packOptions": {
        "requireLicenseAcceptance": true
    }
}
```
   
### <a name="repository"></a>repositório
Tipo: Object

Contém informações sobre o repositório em que o projeto está armazenado.

#### <a name="type"></a>tipo
Tipo: String

Tipo de repositório. O valor padrão é “git”.

Por exemplo:

```json
{
    "packOptions": {
        "repository": {
            "type": "git"
        }
    }
}
```

#### <a name="url"></a>url
Tipo: String

A URL do repositório em que o projeto está armazenado.

Por exemplo:

```json
{
    "packOptions": {
        "repository": {
            "url": "http://github.com/dotnet/corefx"
        }
    }
}
```

### <a name="files"></a>arquivos
Tipo: Object

#### <a name="include"></a>include
Tipo: String ou String[] com um padrão de recurso de curinga.

```json
{
    "include":["wwwroot", "Views"]
}
```

#### <a name="exclude"></a>exclude
Tipo: String ou String[] com um padrão de recurso de curinga.

Especifica quais arquivos serão excluídos do build.

Por exemplo:

```json
{
    "exclude": ["bin/**", "obj/**"]
}
```

#### <a name="includefiles"></a>includeFiles

Tipo: String ou String[] com um padrão de recurso de curinga.

```json
{
    "includeFiles":[]
}
```

#### <a name="excludefiles"></a>excludeFiles

Tipo: String ou String[] com um padrão de recurso de curinga.

```json
{
    "excludeFiles":[]
}
```

#### <a name="builtins"></a>builtIns
Tipo: Object

```json
{
    "builtIns":{}
}
```

#### <a name="mappings"></a>mapeamentos
Tipo: Object

Chaves para o objeto representam caminhos de destino no layout de saída.

Os valores são uma cadeia de caracteres ou um objeto que representa o caminho de origem dos arquivos a serem incluídos.  A representação do objeto pode ter suas próprias seções `include`, `exclude`, `includeFiles` e `excludeFiles`. 

Exemplo de cadeia de caracteres:

```json
{
    "mappings": {
        "dest/path": "./src/path"
    }
}
```

Exemplo de objeto:

```json
{
    "mappings": {
        "dest/path":{
            "include":"./src/path"
        }
    }
}
```

## <a name="analyzeroptions"></a>analyzerOptions
Tipo: Object

Um objeto com propriedades usadas pelos analisadores de código.

Por exemplo:

```json
{
    "analyzerOptions": { }
}
```

### <a name="languageid"></a>languageId
Tipo: String

A ID da linguagem para analisar. “cs” representa C#, “vb” representa Visual Basic e “fs” representa F#.

Por exemplo:

```json
"analyzerOptions": {
    "languageId": "vb"
}
```

## <a name="configurations"></a>configurações
Tipo: Object

Um objeto cujas propriedades definem configurações diferentes para esse projeto, como Debug e Release. Cada valor é um objeto que pode conter um objeto `buildOptions` com opções específicas para essa configuração.

Por exemplo:

```json
"configurations": {
    "Release": {
        "buildOptions": {
            "allowUnsafe": false
        }
    }
}
```

## <a name="frameworks"></a>estruturas
Tipo: Object

Especifica a quais estruturas esse projeto dá suporte, como o .NET Framework ou a UWP (Plataforma Universal do Windows). Deve ter um TFM (Moniker da Estrutura de Destino) válido. Cada valor é um objeto que pode conter informações específicas dessa estrutura, como `buildOptions`, `analyzerOptions` e `dependencies`, bem como as propriedades nas seções a seguir.

Por exemplo:

```json
"frameworks": {
    "netcoreapp1.0": {
        "buildOptions": {
            "define": ["FOO", "BIZ"]
        }
    }
}
```

### <a name="dependencies"></a>dependências
Tipo: Object

Dependências que são específicas dessa estrutura. Isso é útil em cenários em que simplesmente não é possível especificar uma dependência no nível do pacote em todos os destinos. Os motivos para isso podem incluir um destino que não tem suporte interno que os demais destinos têm ou exigir uma versão diferente de uma dependência de outros destinos. Para ver uma lista das outras propriedades para esse nó, consulte a seção [dependências](#dependencies) anterior.

Por exemplo:

```json
    "frameworks": {
        "netstandard1.5": {
        "dependencies": {
            "Microsoft.Extensions.JsonParser.Sources": "1.0.0-rc2-20221"
        }
    }
}
```

### <a name="frameworkassemblies"></a>frameworkAssemblies
Tipo: Object

Semelhante às dependências, mas contém referência aos assemblies no GAC que não são pacotes NuGet. Também é possível especificar a versão a ser usada, bem como o tipo de dependência. Isso é usado ao direcionar para destinos do .NET Framework e da PCL (Biblioteca de Classes Portátil). Somente é possível compilar um projeto com isso especificado no Windows.

Por exemplo:

```json
"frameworks": {
    "net451": {
        "frameworkAssemblies": {
            "System.Runtime": {
                "type": "build",
                "version": "4.0.0"
            }
        }
    }
}
```

### <a name="wrappedproject"></a>wrappedProject
Tipo: String

Especifica o local do projeto de dependência. 

Por exemplo:

```json
"frameworks": {
    "net451": {
        "wrappedProject": "MyProject.csproj"
    }
}
```

### <a name="bin"></a>bin
Tipo: Object

Isso é usado para encapsular um arquivo DLL. Você pode referenciar e gerar um pacote que contém essa DLL. 

Ele contém uma única propriedade String, `assembly`, cujo valor é o caminho do assembly.   

Por exemplo:

```json
"frameworks": {
    "netcoreapp1.0": {
        "bin": {
            "assembly": "c:/otherProject/otherdll.dll"
        }
    }
}
```

## <a name="runtimes"></a>runtimes
Tipo: Object

Lista os [RIDs (Identificadores de Tempo de Execução)](../rid-catalog.md) com suporte no projeto (usados ao publicar [implantações autocontidas](../deploying/index.md#self-contained-deployments-scd)).

Por exemplo:

```json
"runtimes": {
    "win7-x64": {},
    "win8-x64": {},
    "win81-x64": {},
    "win10-x64": {},
    "osx.10.11-x64": {},
    "ubuntu.16.04-x64": {}
}
```

## <a name="usersecretsid"></a>userSecretsId
Tipo: String

Especifica um identificador secreto do usuário a ser usado no tempo de desenvolvimento. Para obter mais informações, consulte o [Armazenamento seguro dos segredos do aplicativo durante o desenvolvimento](https://docs.asp.net/en/latest/security/app-secrets.html).

Por exemplo:

```json
{
    "userSecretsId": "aspnet-WebApp1-c23d27a4-eb88-4b18-9b77-2a93f3b15119"
}
```



<!--HONumber=Nov16_HO3-->


