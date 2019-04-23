---
title: Selecionar a versão da linguagem C# – Guia do C#
description: Configure o compilador para executar a validação de sintaxe usando uma versão específica de compilador
ms.date: 02/28/2019
ms.openlocfilehash: feb3e51a107f9830071b55c7985f202edc842f4a
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59480736"
---
# <a name="select-the-c-language-version"></a>Selecionar a versão da linguagem C#

O compilador C# determina uma versão da linguagem padrão com base na estrutura de destino ou nas estruturas de seu projeto. Quando seu projeto se destina a uma estrutura de visualização que tem uma versão da linguagem correspondente da visualização, a versão de linguagem usada é a de visualização. Quando seu projeto não tem como alvo uma estrutura de visualização, a versão de linguagem usada é a versão secundária mais recente.

Por exemplo, durante o período de visualização do .NET Core 3.0, qualquer projeto que tem como alvo `netcoreapp3.0` ou `netstandard2.1` (ambas na visualização) usará a linguagem C# 8.0 (também em visualização). Projetos direcionados para qualquer versão de lançamento usarão o C# 7.3 (a versão lançada mais recente). Esse comportamento significa que qualquer projeto direcionado ao .NET Framework usará a versão mais recente (C# 7.3). 

Essa funcionalidade separa a decisão de instalar novas versões do SDK e das ferramentas no ambiente de desenvolvimento da decisão de incorporar novas funcionalidades da linguagem em um projeto. Instale o último SDK e as últimas ferramentas no computador de build. Cada projeto pode ser configurado para usar uma versão específica da linguagem de seu build. O comportamento padrão significa que os recursos de linguagem que se baseiam em novos tipos ou novo comportamento CLR são habilitados somente quando os projetos se destinam a essas estruturas.

Você pode substituir o comportamento padrão especificando uma versão da linguagem. Há várias maneiras de definir a versão da linguagem:

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
|versão prévia|O compilador aceita todas as sintaxes de linguagem válidas da versão prévia mais recente.|
|mais recente|O compilador aceita a sintaxe da versão lançada mais recente do compilador (incluindo a versão secundária).|
|latestMajor|O compilador aceita a sintaxe da versão principal mais recente lançada do compilador.|
|8.0|O compilador aceita somente a sintaxe incluída no C# 8.0 ou inferior.|
|7.3|O compilador aceita somente a sintaxe incluída no C# 7.3 ou inferior.|
|7.2|O compilador aceita somente a sintaxe incluída no C# 7.2 ou inferior.|
|7.1|O compilador aceita somente a sintaxe incluída no C# 7.1 ou inferior.|
|7|O compilador aceita somente a sintaxe incluída no C# 7.0 ou inferior.|
|6|O compilador aceita somente a sintaxe incluída no C# 6.0 ou inferior.|
|5|O compilador aceita somente a sintaxe incluída no C# 5.0 ou inferior.|
|4|O compilador aceita somente a sintaxe incluída no C# 4.0 ou inferior.|
|3|O compilador aceita somente a sintaxe incluída no C# 3.0 ou inferior.|
|ISO-2|O compilador aceita somente a sintaxe incluída no ISO/IEC 23270:2006 C# (2.0) |
|ISO-1|O compilador aceita somente a sintaxe incluída no ISO/IEC 23270:2003 C# (1.0/1.2) |

## <a name="configure-multiple-projects"></a>Configurar vários projetos

Crie um arquivo **Directory.Build.props** que contém o elemento `<LangVersion>` para configurar vários diretórios. Normalmente, você faz isso no diretório da solução. Adicione o seguinte a um arquivo **Directory.Build.props** no diretório de solução:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>7.3</LangVersion>
 </PropertyGroup>
</Project>
```

Agora, os builds de cada subdiretório do diretório que contém esse arquivo usarão a sintaxe C# versão 7.3. Para obter mais informações, confira o artigo sobre como [personalizar o build](/visualstudio/msbuild/customize-your-build).

## <a name="set-the-langversion-compiler-option"></a>Definir a opção langversion do compilador

Você pode usar a opção `-langversion` da linha de comando. Para obter mais informações, confira o artigo sobre a opção [-langversion](../language-reference/compiler-options/langversion-compiler-option.md) do compilador. Veja uma lista dos valores válidos digitando `csc -langversion:?`.
