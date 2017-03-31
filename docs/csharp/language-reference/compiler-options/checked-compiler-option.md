---
title: "-checked (Opções do compilador C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /checked
dev_langs:
- CSharp
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
caps.latest.revision: 20
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c6cfc54c2dbd3e14d874d7684fdc75a972260cc3
ms.lasthandoff: 03/13/2017

---
# <a name="checked-c-compiler-options"></a>/checked (opções do compilador C#)
A opção **/checked** especifica se uma instrução de aritmética de inteiros que resulta em um valor fora do intervalo do tipo de dados e que não está no escopo de uma palavra-chave [checked](../../../csharp/language-reference/keywords/checked.md) ou [unchecked](../../../csharp/language-reference/keywords/unchecked.md), causará uma exceção de tempo de execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/checked[+ | -]  
```  
  
## <a name="remarks"></a>Comentários  
 Uma instrução de aritmética de inteiros que está no escopo de uma palavra-chave `checked` ou `unchecked` não está sujeita ao efeito da opção **/checked**.  
  
 Se uma instrução de aritmética de inteiros que não está no escopo de uma palavra-chave `checked` ou `unchecked` resultar em um valor fora do intervalo do tipo de dados e **/checked+** (**/checked**) for usado na compilação, a instrução causará uma exceção em tempo de execução. Se **/checked-** for usado na compilação, a instrução não causará uma exceção em tempo de execução.  
  
 O valor padrão desta opção é **/checked-**. Um cenário de uso de **/checked-** é a compilação de aplicativos grandes. Às vezes, ferramentas automatizadas são usadas para compilar esses aplicativos e a ferramenta pode definir automaticamente **/checked** como +. Você pode substituir o padrão global da ferramenta especificando **/checked-**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página **Propriedades** do projeto. Para obter mais informações, consulte [Página Build, Designer de Projeto (C#)](https://docs.microsoft.com/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2.  Clique na página de propriedades **Compilar**.  
  
3.  Clique no botão **Avançado**.  
  
4.  Modifique a propriedade **Procurar estouro/estouro negativo aritmético**.  
  
 Para acessar essa opção do compilador de maneira programática, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.  
  
## <a name="example"></a>Exemplo  
 O comando a seguir compila `t2.cs`. O uso de `/checked` no comando especifica que qualquer instrução de aritmética de inteiros no arquivo que não está no escopo de uma palavra-chave `checked` ou `unchecked` e que resulta em um valor fora do intervalo do tipo de dados, causa uma exceção em tempo de execução.  
  
```  
csc t2.cs /checked  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB: Como Modificar as Propriedades do Projeto e as Definições de Configuração](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)
