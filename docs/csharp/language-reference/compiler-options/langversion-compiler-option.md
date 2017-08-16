---
title: "-langversion (opções do compilador C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /langversion
dev_langs:
- CSharp
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
caps.latest.revision: 33
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: fc501c5532d27168d74d1a5f293abe59d3beeef1
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="langversion-c-compiler-options"></a>/langversion (opções do compilador C#)
Faz com que o compilador aceite somente a sintaxe incluída na especificação de linguagem C# escolhida.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
/langversion:option  
```  
  
## <a name="arguments"></a>Arguments  
 `option`  
 Os seguintes valores são válidos:  
  
|Opção|Significado|  
|------------|-------------|  
|default|O compilador aceita toda a sintaxe de linguagem à qual dá suporte. <sup id="TDefault">[Padrão](#FDefault)</sup>| 
|ISO-1|O compilador aceita somente a sintaxe incluída em C# ISO/IEC 23270:2003 (1.0/1.1) <sup id="TISO1">[ISO1](#FISO1)</sup>|  
|ISO-2|O compilador aceita somente a sintaxe incluída em C# ISO/IEC 23270:2006 (2.0) <sup id="TISO2">[ISO2](#FISO2)</sup>|
|3|O compilador aceita somente a sintaxe incluída em C# 3.0 ou inferior <sup id="TCS3">[CS3](#FCS3)</sup>|
|4|O compilador aceita somente a sintaxe incluída em C# 4.0 ou inferior <sup id="TCS4">[CS4](#FCS4)</sup>|
|5|O compilador aceita somente a sintaxe incluída em C# 5.0 ou inferior <sup id="TCS5">[CS5](#FCS5)</sup>|
|6|O compilador aceita somente a sintaxe incluída em C# 6.0 ou inferior <sup id="TCS6">[CS6](#FCS6)</sup>|
|7|O compilador aceita somente a sintaxe incluída em C# 7.0 ou inferior <sup id="TCS7">[CS7](#FCS7)</sup>|
|mais recente|O compilador aceita toda a sintaxe de linguagem à qual dá suporte. <sup id="TLatest">[Mais recente](#FLatest)</sup>|
<!--- Uncomment and move these above
|latest| once they're officially released
|7.1|The compiler accepts only syntax that is included in C# 7.1 or lower <sup id="TCS71">[CS71](#FCS71)</sup>|
|7.2|The compiler accepts only syntax that is included in C# 7.2 or lower <sup id="TCS71">[CS72](#FCS72)</sup>|
|8|The compiler accepts only syntax that is included in C# 8 or lower <sup id="TCS71">[CS8](#FCS8)</sup>|
-->

  
## <a name="remarks"></a>Comentários  
 Metadados referenciados pelo seu aplicativo C# não estão sujeitos à opção do compilador **/langversion**.  
  
 Como cada versão do compilador C# contém extensões para a especificação de linguagem, **/langversion** não dá a funcionalidade equivalente de uma versão anterior do compilador.  
 
 Além disso, embora as atualizações de versão C# geralmente coincidam com os principais lançamentos do .NET Framework, a nova sintaxe e os recursos não estão necessariamente vinculados a essa versão específica da estrutura. Embora os novos recursos definitivamente exigirão uma nova atualização de compilador que também é lançada junto com a revisão do C#, cada recurso específico tem seus próprios requisitos mínimos de .NET API ou de Common Language Runtime que podem permitir que ele seja executado em estruturas de nível inferior, incluindo pacotes do NuGet ou outras bibliotecas.
  
 Independentemente de qual configuração **/langversion** você usa, você usará a versão atual do Common Language Runtime para criar seu .exe ou. dll. Uma exceção são os assemblies amigáveis e [/moduleassemblyname (Opção do compilador C#)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md), que funcionam em **/langversion:ISO-1**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página **Propriedades** do projeto.  
  
2.  Clique na página de propriedades **Compilar**.  
  
3.  Clique no botão **Avançado**.  
  
4.  Modifique a propriedade **Versão da Linguagem**.  
  
 Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.  
    
## <a name="see-also"></a>Consulte também  
 [Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md)   
 [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)   
 
### <a name="c-language-specification"></a>Especificação da Linguagem C#
 [Referência de Especificação da Linguagem C#](../../../csharp/language-reference/language-specification/index.md): .NET Foundation   
 C# 1.0/1.1 [23270:2003 ISO/IEC](https://www.iso.org/standard/36768.html) Tecnologia da informação – Especificação da Linguagem C#: catálogo de ISO   
 C# 2.0 [ISO/IEC 23270:2006](https://www.iso.org/standard/42926.html) Tecnologia da informação – Especificação da Linguagem C#: catálogo de ISO   
 C# 2.0 [c042926_ISO_IEC_23270_2006(E).zip](http://go.microsoft.com/fwlink/?LinkId=144406) ISO/IEC 23270:2006 em formato PDF: padrões ISO disponíveis gratuitamente   
 C# 3.0 [CSharp Language Specification.doc](http://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc) Versão de Especificação da Linguagem C# 3.0: Microsoft Corporation   
 C# 4.0 [Ecma-334.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/Ecma-334.pdf) ECMA-334 Standard 4a Edição    
 C# 5.0 [CSharp Language Specification.doc](https://www.microsoft.com/en-us/download/details.aspx?id=7029) Versão de Especificação da Linguagem C# 5.0: Microsoft Corporation   
 C# 6.0 [README.md](https://github.com/dotnet/csharplang/blob/master/spec/README.md) Versão de Especificação da Linguagem C# 6 – rascunho não oficial: .NET Foundation   
 C# 7.0 (não disponível no momento)   

<!--- Uncomment and add to the above when they become officially released
 C# 7.1 (spec is not yet finished)   
 C# 7.2 (spec is not yet finished)   
 C# 8.0 (spec is not yet finished)   
-->

### <a name="minimum-compiler-version-needed-to-support-all-language-features"></a>Versão mínima do compilador necessária para dar suporte a todos os recursos de idioma   
[↩](#TDefault)<a name="FDefault">Padrão</a>, <a name="FISO1">ISO1</a>: Ferramentas de Build/Microsoft Visual Studio .Net 2002 ou compilador do .NET Framework 1.0 no pacote     
[↩](#TISO2)<a name="FISO2">ISO2</a>: Ferramentas de Build/Microsoft Visual Studio 2005 ou compilador do .NET Framework 2.0 no pacote    
[↩](#TCS3)<a name="FCS3">CS3</a>: Ferramentas de Build/Microsoft Visual Studio 2008 ou compilador do .NET Framework 3.5 no pacote    
[↩](#TCS4)<a name="FCS4">CS4</a>: Ferramentas de Build/Microsoft Visual Studio 2010 ou compilador do .NET Framework 4.0 no pacote    
[↩](#TCS5)<a name="FCS5">CS5</a>: Ferramentas de Build/Microsoft Visual Studio 2012 ou compilador do .NET Framework 4.5 no pacote    
[↩](#TCS6)<a name="FCS6">CS6</a>: Ferramentas de Build/Microsoft Visual Studio 2015    
[↩](#TCS7)<a name="FCS7">CS7</a>, <a name="FLatest">mais recente</a>: Ferramentas de Build/Microsoft Visual Studio 2017   

<!--- Uncomment and add to the above when they become officially released
[↩](#TCS71)<a name="FCS71">CS71</a>: Microsoft Visual Studio/Build Tools 20??    
[↩](#TCS72)<a name="FCS72">CS72</a>: Microsoft Visual Studio/Build Tools 20??    
[↩](#TCS8)<a name="FCS71">CS8</a>: Microsoft Visual Studio/Build Tools 20??    
-->

