---
title: -langversion (opções do compilador C#)
ms.date: 08/23/2019
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: 81cf336f94815dd3f2c88995eb34ae03b8220097
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179915"
---
# <a name="-langversion-c-compiler-options"></a>-langversion (opções do compilador C#)

Faz com que o compilador aceite somente a sintaxe incluída na especificação de linguagem C# escolhida.

## <a name="syntax"></a>Sintaxe

```console
-langversion:option
```

## <a name="arguments"></a>Argumentos

 `option`  
 Os seguintes valores são válidos:

|Opção|Significado|
|------------|-------------|
|versão prévia|O compilador aceita toda as sintaxes de linguagem válidas da versão prévia mais recente à qual dá suporte.|
|latest|O compilador aceita toda as sintaxes de linguagem válidas da versão (incluindo versões secundárias) mais recente à qual dá suporte.|
|latestMajor|O compilador aceita toda a sintaxe de linguagem válida da versão principal mais recente à qual dá suporte.|
|8.0|O compilador aceita somente a sintaxe incluída no C# 8.0 ou inferior.|
|7.3|O compilador aceita somente a sintaxe incluída no C# 7.3 ou inferior.|
|7.2|O compilador aceita somente a sintaxe incluída no C# 7.2 ou inferior.|
|7.1|O compilador aceita somente a sintaxe incluída no C# 7.1 ou inferior.|
|7|O compilador aceita somente a sintaxe incluída no C# 7.0 ou inferior.|
|6|O compilador aceita somente a sintaxe incluída no C# 6.0 ou inferior.|
|5|O compilador aceita somente a sintaxe incluída no C# 5.0 ou inferior.|
|4|O compilador aceita somente a sintaxe incluída no C# 4.0 ou inferior.|
|3|O compilador aceita somente a sintaxe incluída no C# 3.0 ou inferior.|
|ISO-2|O compilador aceita apenas a sintaxe que está incluída no ISO/IEC C# 23270:2006 (2,0).|
|ISO-1|O compilador aceita apenas a sintaxe que está incluída no ISO/IEC C# 23270:2003 (1.0/1.2).|

A versão da linguagem padrão depende da estrutura de destino do aplicativo e da versão do SDK ou do Visual Studio instalado. Essas regras são definidas no artigo [Configurando a versão do idioma](../configure-language-version.md#defaults) .

## <a name="remarks"></a>Comentários

Os metadados referenciados pelo seu aplicativo de C# não estão sujeitos à opção do compilador **-langversion**.
  
Como cada versão do compilador do C# contém extensões para a especificação de linguagem, **-langversion** não dá a funcionalidade equivalente de uma versão anterior do compilador.

Além disso, embora as atualizações de versão do C# geralmente coincidam com as versões principais do .NET Framework, a nova sintaxe e as funcionalidades não estão necessariamente vinculadas a essa versão de estrutura específica. Embora as novas funcionalidades definitivamente exijam uma nova atualização do compilador que também é liberada junto com a revisão do C#, cada funcionalidade específica tem seus próprios requisitos mínimos de API ou do Common Language Runtime do .NET que podem permitir que ela seja executada em estruturas de nível inferior com a inclusão de pacotes NuGet ou de outras bibliotecas.

Independentemente de qual configuração **-langversion** for usada, você usará a versão atual do Common Language Runtime para criar seu .exe ou .dll. Uma exceção são os assemblies amigáveis e [-moduleassemblyname (Opção do compilador do C#)](./moduleassemblyname-compiler-option.md), que funcionarão em **-langversion:ISO-1**.  

Para outras maneiras de especificar a C# versão do idioma, consulte o artigo [selecionar a versão C# do idioma](../configure-language-version.md) .

Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.

## <a name="c-language-specification"></a>Especificação da linguagem C#

|Versão|Link|Descrição|
|-------|----|-----------|
|C# 7.0 e posterior||não disponível atualmente|
|C# 6.0|[Link](../language-specification/index.md)|Especificação da Linguagem C# Versão 6 – Rascunho não oficial: .NET Foundation|
|C# 5.0|[Baixar PDF](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)|Padrão ECMA-334 – 5ª Edição|
|C# 3.0|[Baixar DOC](https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc)|Especificação da linguagem C# versão 3.0: Microsoft Corporation|
|C# 2.0|[Baixar PDF](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf)|Padrão ECMA-334 – 4ª Edição|
|C# 1.2|[Baixar DOC](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf)|Especificação da linguagem C# versão 1.2: Microsoft Corporation|
|C# 1.0|[Baixar DOC](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf)|Especificação da linguagem C# versão 1.0: Microsoft Corporation|

## <a name="minimum-sdk-version-needed-to-support-all-language-features"></a>Versão mínima do SDK necessária para dar suporte a todos os recursos de idioma

A tabela a seguir lista as versões mínimas do SDK com C# o compilador que dá suporte à versão de idioma correspondente:

|C#Versão|Versão mínima do SDK|
|----------|-------------------|
|C# 8.0| Ferramentas de Microsoft Visual Studio/Build 2019, versão 16,3 ou SDK do .NET Core 3,0 |
|C# 7.3| Microsoft Visual Studio/Ferramentas de Build 2017, versão 15.7 |
|C# 7.2| Microsoft Visual Studio/Ferramentas de Build 2017, versão 15.5 |
|C# 7.1| Microsoft Visual Studio/Ferramentas de Build 2017, versão 15.3 |
|C# 7.0| Microsoft Visual Studio/Ferramentas de Build 2017 |
|C# 6| Microsoft Visual Studio/Ferramentas de Build 2015 |
|C#05| Microsoft Visual Studio/Ferramentas de Build 2012 ou compilador do .NET Framework 4.5 em pacote |
|C# 4| Microsoft Visual Studio/Ferramentas de Build 2010 ou compilador do .NET Framework 4.0 em pacote |
|C#BETA| Microsoft Visual Studio/Ferramentas de Build 2008 ou compilador do .NET Framework 3.5 em pacote |
|C#2| Microsoft Visual Studio/Ferramentas de Build 2005 ou compilador do .NET Framework 2.0 em pacote |
|C#1,0/1.2 | Compilador de ferramentas Microsoft Visual Studio/Build .NET 2002 ou pacotes .NET Framework 1,0 em pacote |

## <a name="see-also"></a>Consulte também

- [Opções do compilador de C#](index.md)
- [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
