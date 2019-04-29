---
title: Selecione a versão da linguagem Visual Basic
description: Configure o compilador para executar a validação de sintaxe usando uma versão específica do compilador.
ms.date: 05/24/2018
ms.openlocfilehash: 3b6d8055dbf64f2a5c38f46b6d66794fc48a1cea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797014"
---
# <a name="select-the-visual-basic-language-version"></a>Selecione a versão da linguagem Visual Basic

O compilador do Visual Basic usa como padrão para a versão principal mais recente da linguagem que foi lançada. Você pode optar por compilar qualquer projeto usando uma nova versão de ponto da linguagem. A escolha de uma versão mais recente da linguagem permite que o projeto use as últimas funcionalidades da linguagem. Em outros cenários, talvez você precise validar se um projeto é compilado por completo ao usar uma versão mais antiga da linguagem.

Essa funcionalidade separa a decisão de instalar novas versões do SDK e das ferramentas no ambiente de desenvolvimento da decisão de incorporar novas funcionalidades da linguagem em um projeto. Instale o último SDK e as últimas ferramentas no computador de build. Cada projeto pode ser configurado para usar uma versão específica da linguagem de seu build.

Há três maneiras de definir a versão de idioma:

- Editar manualmente sua [ **. vbproj** arquivo](#edit-the-vbproj-file)
- Defina a versão de idioma [para vários projetos em um subdiretório](#configure-multiple-projects)
- Configurar o [ `-langversion` opção de compilador](#set-the-langversion-compiler-option)

## <a name="edit-the-vbproj-file"></a>Edite o arquivo vbproj

Você pode definir a versão de idioma no seu **. vbproj** arquivo. Adicione o seguinte elemento:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

O valor `latest` usa a versão secundária mais recente da linguagem Visual Basic. Os valores válidos são:

|Valor|Significado|
|------------|-------------|
|default|O compilador aceita toda a sintaxe de linguagem válida da versão principal mais recente à qual dá suporte.|
|9|O compilador aceita somente a sintaxe incluída no Visual Basic 9.0 ou inferior.|
|10|O compilador aceita somente a sintaxe incluída no Visual Basic 10.0 ou inferior.|
|11|O compilador aceita somente a sintaxe incluída no Visual Basic 11.0 ou inferior.|
|12|O compilador aceita somente a sintaxe incluída no Visual Basic 12.0 ou inferior.|
|14|O compilador aceita somente a sintaxe incluída no Visual Basic 14.0 ou inferior.|
|15|O compilador aceita somente a sintaxe incluída em 15.0 do Visual Basic ou inferior.|
|15.3|O compilador aceita somente a sintaxe incluída na versão 15.3 do Visual Basic ou inferior.|
|15.5|O compilador aceita somente a sintaxe incluída na versão 15.5 do Visual Basic ou inferior.|
|mais recente|O compilador aceita toda a sintaxe de linguagem à qual dá suporte.|

As cadeias de caracteres especiais `default` e `latest` são resolvidas nas últimas versões da linguagem principal e secundária instaladas no computador de build, respectivamente.

## <a name="configure-multiple-projects"></a>Configurar vários projetos

Crie um arquivo **Directory.build.props** que contém o elemento `<LangVersion>` para configurar vários diretórios. Normalmente, você faz isso no diretório da solução. Adicione o seguinte a um arquivo **Directory.build.props** no diretório de solução:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>15.5</LangVersion>
 </PropertyGroup>
</Project>
```

Agora, compilações em cada subdiretório do diretório que contém esse arquivo serão usar sintaxe de versão 15.5 do Visual Basic. Para obter mais informações, confira o artigo sobre como [personalizar o build](/visualstudio/msbuild/customize-your-build).

## <a name="set-the-langversion-compiler-option"></a>Definir a opção langversion do compilador

Você pode usar a opção `-langversion` da linha de comando. Para obter mais informações, confira o artigo sobre a opção [-langversion](../reference/command-line-compiler/langversion.md) do compilador. Você pode ver uma lista dos valores válidos, digitando `vbc -langversion:?` .
