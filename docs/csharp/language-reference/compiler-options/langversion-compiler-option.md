---
title: -langversion (opções do compilador C#)
ms.date: 05/14/2018
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: 030af5df222772b1e5a4d6f6946e59f4f2d1e1a9
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66195807"
---
# <a name="-langversion-c-compiler-options"></a>-langversion (opções do compilador C#)

Faz com que o compilador aceite somente a sintaxe incluída na especificação de linguagem C# escolhida.  
  
## <a name="syntax"></a>Sintaxe  

```console
-langversion:option  
```

## <a name="arguments"></a>Arguments

 `option`  
 Os seguintes valores são válidos:  
  
|Opção|Significado|  
|------------|-------------|  
|versão prévia|O compilador aceita toda as sintaxes de linguagem válidas da versão prévia mais recente à qual dá suporte.|
|mais recente|O compilador aceita toda as sintaxes de linguagem válidas da versão (incluindo versões secundárias) mais recente à qual dá suporte.|
|latestMajor|O compilador aceita toda a sintaxe de linguagem válida da versão principal mais recente à qual dá suporte.|
|8.0|O compilador aceita somente a sintaxe incluída no C# 8.0 ou inferior. <sup id="TCS80">[CS80](#FCS80)</sup>|
|7.3|O compilador aceita somente a sintaxe incluída em C# 7.3 ou inferior <sup id="TCS73">[CS73](#FCS73)</sup>|
|7.2|O compilador aceita somente a sintaxe incluída em C# 7.2 ou inferior <sup id="TCS72">[CS72](#FCS72)</sup>|
|7.1|O compilador aceita somente a sintaxe incluída em C# 7.1 ou inferior <sup id="TCS71">[CS71](#FCS71)</sup>|
|7|O compilador aceita somente a sintaxe incluída em C# 7.0 ou inferior <sup id="TCS7">[CS7](#FCS7)</sup>|
|6|O compilador aceita somente a sintaxe incluída em C# 6.0 ou inferior <sup id="TCS6">[CS6](#FCS6)</sup>|
|5|O compilador aceita somente a sintaxe incluída em C# 5.0 ou inferior <sup id="TCS5">[CS5](#FCS5)</sup>|
|4|O compilador aceita somente a sintaxe incluída em C# 4.0 ou inferior <sup id="TCS4">[CS4](#FCS4)</sup>|
|3|O compilador aceita somente a sintaxe incluída em C# 3.0 ou inferior <sup id="TCS3">[CS3](#FCS3)</sup>|
|ISO-2|O compilador aceita somente a sintaxe incluída em C# ISO/IEC 23270:2006 (2.0) <sup id="TISO2">[ISO2](#FISO2)</sup>|
|ISO-1|O compilador aceita somente a sintaxe incluída no ISO/IEC 23270:2003 C# (1.0/1.2) <sup id="TISO1">[ISO1](#FISO1)</sup>|  

## <a name="remarks"></a>Comentários

 Os metadados referenciados pelo seu aplicativo de C# não estão sujeitos à opção do compilador **-langversion**.  
  
 Como cada versão do compilador do C# contém extensões para a especificação de linguagem, **-langversion** não dá a funcionalidade equivalente de uma versão anterior do compilador.  

 Além disso, embora as atualizações de versão do C# geralmente coincidam com as versões principais do .NET Framework, a nova sintaxe e as funcionalidades não estão necessariamente vinculadas a essa versão de estrutura específica. Embora as novas funcionalidades definitivamente exijam uma nova atualização do compilador que também é liberada junto com a revisão do C#, cada funcionalidade específica tem seus próprios requisitos mínimos de API ou do Common Language Runtime do .NET que podem permitir que ela seja executada em estruturas de nível inferior com a inclusão de pacotes NuGet ou de outras bibliotecas.
  
 Independentemente de qual configuração **-langversion** for usada, você usará a versão atual do Common Language Runtime para criar seu .exe ou .dll. Uma exceção são os assemblies amigáveis e [-moduleassemblyname (Opção do compilador do C#)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md), que funcionarão em **-langversion:ISO-1**.  

 Para descobrir outras maneiras de especificar a versão da linguagem do C#, confira o tópico [Selecionar a versão da linguagem do C#](../configure-language-version.md).
  
 Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.  

## <a name="see-also"></a>Consulte também

- [Opções do compilador de C#](index.md)
- [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)

### <a name="c-language-specification"></a>Especificação da Linguagem C#

|Versão|Link|Descrição|
|-------|----|-----------|
|C# 7.0 e posterior||não disponível atualmente|
|C# 6.0|[Link](../language-specification/index.md)|Especificação da Linguagem C# Versão 6 – Rascunho não oficial: .NET Foundation|
|C# 5.0|[Baixar PDF](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)|Padrão ECMA-334 – 5ª Edição|
|C# 3.0|[Baixar DOC](https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc)|Especificação da linguagem C# versão 3.0: Microsoft Corporation|
|C# 2.0|[Baixar PDF](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf)|Padrão ECMA-334 – 4ª Edição|
|C# 1.2|[Baixar DOC](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf)|Especificação da linguagem C# versão 1.2: Microsoft Corporation|
|C# 1.0|[Baixar DOC](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf)|Especificação da linguagem C# versão 1.0: Microsoft Corporation|

### <a name="minimum-compiler-version-needed-to-support-all-language-features"></a>Versão mínima do compilador necessária para dar suporte a todos os recursos de idioma

[↩](#TCS80)<a name="FCS80">CS80</a>: Microsoft Visual Studio/Ferramentas de Build 2019, versão 16 ou SDK do .NET Core 3.0  
[↩](#TCS73)<a name="FCS73">CS73</a>: Microsoft Visual Studio/Ferramentas de Build 2017, versão 15.7  
[↩](#TCS72)<a name="FCS72">CS72</a>: Microsoft Visual Studio/Ferramentas de Build 2017, versão 15.5  
[↩](#TCS71)<a name="FCS71">CS71</a>: Microsoft Visual Studio/Ferramentas de Build 2017, versão 15.3  
[↩](#TCS7)<a name="FCS7">CS7</a>: Microsoft Visual Studio/Ferramentas de Build 2017  
[↩](#TCS6)<a name="FCS6">CS6</a>: Microsoft Visual Studio/Ferramentas de Build 2015  
[↩](#TCS5)<a name="FCS5">CS5</a>: Microsoft Visual Studio/Ferramentas de Build 2012 ou compilador do .NET Framework 4.5 em pacote  
[↩](#TCS4)<a name="FCS4">CS4</a>: Microsoft Visual Studio/Ferramentas de Build 2010 ou compilador do .NET Framework 4.0 em pacote  
[↩](#TCS3)<a name="FCS3">CS3</a>: Microsoft Visual Studio/Ferramentas de Build 2008 ou compilador do .NET Framework 3.5 em pacote  
[↩](#TISO2)<a name="FISO2">ISO2</a>: Microsoft Visual Studio/Ferramentas de Build 2005 ou compilador do .NET Framework 2.0 em pacote  
[↩](#TISO1)<a name="FISO1">ISO1</a>: Microsoft Visual Studio/Ferramentas de Build 2002 ou compilador do .NET Framework 1.0 em pacote  
