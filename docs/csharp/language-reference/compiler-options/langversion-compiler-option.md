---
title: "-langversion (Opções do compilador do C#) | Microsoft Docs"
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2119e5f5b244d5c1447032025d1a40ce782e8d4d
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

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
|default|O compilador aceita toda a sintaxe de linguagem válida.|  
|ISO-1|O compilador aceita somente a sintaxe incluída na especificação de linguagem C# ISO/IEC 23270:2003.|  
|ISO-2|O compilador aceita somente a sintaxe incluída na especificação de linguagem C# ISO/IEC 23270:2006. Essa especificação está disponível no site da Web [ISO](http://go.microsoft.com/fwlink/?LinkId=144406).|  
|3|O compilador aceita somente a sintaxe incluída na [Especificação de Linguagem C#](../../../csharp/language-reference/language-specification.md) versão 3.0.|  
  
## <a name="remarks"></a>Comentários  
 Metadados referenciados pelo seu aplicativo C# não estão sujeitos à opção do compilador **/langversion**.  
  
 Como cada versão do compilador C# contém extensões para a especificação de linguagem, **/langversion** não dá a funcionalidade equivalente de uma versão anterior do compilador.  
  
 Independentemente de qual configuração **/langversion** você usa, você usará a versão atual do Common Language Runtime para criar seu .exe ou. dll. Uma exceção são os assemblies amigáveis e [/moduleassemblyname (Opção do compilador C#)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md), que funcionam em **/langversion:ISO-1**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página **Propriedades** do projeto.  
  
2.  Clique na página de propriedades **Compilar**.  
  
3.  Clique no botão **Avançado**.  
  
4.  Modifique a propriedade **Versão da Linguagem**.  
  
 Para obter informações sobre como definir essa opção do compilador de maneira programática, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB: Como Modificar as Propriedades do Projeto e as Definições de Configuração](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [C# Language Specification](../../../csharp/language-reference/language-specification.md) (Especificação da linguagem C#)
