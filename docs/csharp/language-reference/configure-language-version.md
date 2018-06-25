---
title: Selecionar a versão da linguagem C# – Guia do C#
description: Configure o compilador para executar a validação de sintaxe usando uma versão específica de compilador
ms.date: 05/24/2018
ms.openlocfilehash: 2056a99544d0cac94bc7cc79e8cd8793b1bcff78
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34566303"
---
# <a name="select-the-c-language-version"></a>Selecionar a versão da linguagem C#

O compilador C# usa como padrão a última versão principal da linguagem que foi liberada. Você pode optar por compilar qualquer projeto usando uma nova versão de ponto da linguagem. A escolha de uma versão mais recente da linguagem permite que o projeto use as últimas funcionalidades da linguagem. Em outros cenários, talvez você precise validar se um projeto é compilado por completo ao usar uma versão mais antiga da linguagem.

Essa funcionalidade separa a decisão de instalar novas versões do SDK e das ferramentas no ambiente de desenvolvimento da decisão de incorporar novas funcionalidades da linguagem em um projeto. Instale o último SDK e as últimas ferramentas no computador de build. Cada projeto pode ser configurado para usar uma versão específica da linguagem de seu build.

Há várias maneiras de definir a versão da linguagem:

- Depender de uma [ação rápida do Visual Studio](#visual-studio-quick-action).
- Definir a versão da linguagem na [interface do usuário do Visual Studio](#set-the-language-version-in-visual-studio).
- Editar manualmente o arquivo [**.csproj**](#edit-the-csproj-file).
- Definir a versão da linguagem [para vários projetos em um subdiretório](#configure-multiple-projects).
- Configurar a opção [`-langversion` do compilador](#set-the-langversion-compiler-option).

## <a name="visual-studio-quick-action"></a>Ação rápida do Visual Studio

O Visual Studio ajuda você a determinar a versão da linguagem necessária. Se você usar uma funcionalidade de linguagem que não está disponível para a versão atualmente configurada, o Visual Studio mostrará uma correção potencial para atualizar a versão da linguagem do projeto.

## <a name="set-the-language-version-in-visual-studio"></a>Definir a versão da linguagem no Visual Studio

Você pode definir a versão no Visual Studio. Clique com o botão direito do mouse no nó do projeto no Gerenciador de Soluções e selecione **Propriedades**. Selecione a guia **Build** e o botão **Avançado**. Na lista suspensa, selecione a versão. A seguinte imagem mostra a "última" configuração:

![Captura de tela de configurações avançadas de build nas quais é possível especificar a versão da linguagem](./media/configure-language-version/advanced-build-settings.png)

> [!NOTE]
> Se você usar o IDE do Visual Studio para atualizar os arquivos csproj, o IDE criará nós separados para cada configuração de build. Normalmente, você definirá o valor da mesma forma em todas as configurações de build, mas precisará defini-lo explicitamente para cada configuração de build ou selecionar "Todas as Configurações" ao modificar essa configuração. Você verá o seguinte no arquivo csproj:
>
>```xml
> <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
>  <LangVersion>latest</LangVersion>
></PropertyGroup>
>
> <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
>  <LangVersion>latest</LangVersion>
> </PropertyGroup>
> ```
>

## <a name="edit-the-csproj-file"></a>Editar o arquivo csproj

Você pode definir a versão da linguagem no arquivo **.csproj**. Adicione um elemento como o seguinte:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

O valor `latest` usa a última versão secundária da linguagem C#. Os valores válidos são:

|Valor|Significado|
|------------|-------------|
|default|O compilador aceita toda a sintaxe de linguagem válida da versão principal mais recente à qual dá suporte.|
|ISO-1|O compilador aceita somente a sintaxe incluída no ISO/IEC 23270:2003 C# (1.0/1.2) |
|ISO-2|O compilador aceita somente a sintaxe incluída no ISO/IEC 23270:2006 C# (2.0) |
|3|O compilador aceita somente a sintaxe incluída no C# 3.0 ou inferior.|
|4|O compilador aceita somente a sintaxe incluída no C# 4.0 ou inferior.|
|5|O compilador aceita somente a sintaxe incluída no C# 5.0 ou inferior.|
|6|O compilador aceita somente a sintaxe incluída no C# 6.0 ou inferior.|
|7|O compilador aceita somente a sintaxe incluída no C# 7.0 ou inferior.|
|7.1|O compilador aceita somente a sintaxe incluída no C# 7.1 ou inferior.|
|7.2|O compilador aceita somente a sintaxe incluída no C# 7.2 ou inferior.|
|7.3|O compilador aceita somente a sintaxe incluída no C# 7.3 ou inferior.|
|mais recente|O compilador aceita toda a sintaxe de linguagem à qual dá suporte.|

As cadeias de caracteres especiais `default` e `latest` são resolvidas nas últimas versões da linguagem principal (C# 7.0) e secundária (C# 7.3) instaladas no computador de build, respectivamente.

## <a name="configure-multiple-projects"></a>Configurar vários projetos

Crie um arquivo **Directory.build.props** que contém o elemento `<LangVersion>` para configurar vários diretórios. Normalmente, você faz isso no diretório da solução. Adicione o seguinte a um arquivo **Directory.build.props** no diretório de solução:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>7.3</LangVersion>
 </PropertyGroup>
</Project>
```

Agora, os builds de cada subdiretório do diretório que contém esse arquivo usarão a sintaxe C# versão 7.3. Para obter mais informações, confira o artigo sobre como [personalizar o build](/visualstudio/msbuild/customize-your-build.md).

## <a name="set-the-langversion-compiler-option"></a>Definir a opção langversion do compilador

Você pode usar a opção `-langversion` da linha de comando. Para obter mais informações, confira o artigo sobre a opção [-langversion](../language-reference/compiler-options/langversion-compiler-option.md) do compilador. Veja uma lista dos valores válidos digitando `csc -langversion:?`.
