---
title: "-checked (opções do compilador C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c0a8cc66609fe542fc7db166cd208cfcedb204b8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="-checked-c-compiler-options"></a>-checked (opções do compilador C#)
A opção **-checked** especifica se uma instrução de aritmética de inteiros que resulta em um valor fora do intervalo do tipo de dados e que não está no escopo de uma palavra-chave [checked](../../../csharp/language-reference/keywords/checked.md) ou [unchecked](../../../csharp/language-reference/keywords/unchecked.md), causa uma exceção de tempo de execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a>Comentários  
 Uma instrução de aritmética de inteiros que está no escopo de uma palavra-chave `checked` ou `unchecked` não está sujeita ao efeito da opção **-checked**.  
  
 Se uma instrução de aritmética de inteiros que não está no escopo de uma palavra-chave `checked` ou `unchecked` resultar em um valor fora do intervalo do tipo de dados e **-checked+** (**-checked**) for usado na compilação, a instrução causará uma exceção em tempo de execução. Se **-checked-** for usado na compilação, a instrução não causará uma exceção em tempo de execução.  
  
 O valor padrão desta opção é **-checked-**. Um cenário de uso de **-checked-** é a compilação de aplicativos grandes. Às vezes, ferramentas automatizadas são usadas para compilar esses aplicativos e esse tipo de ferramenta pode definir automaticamente **-checked** como +. Você pode substituir o padrão global da ferramenta especificando **-checked-**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página **Propriedades** do projeto. Para obter mais informações, consulte [Página Build, Designer de Projeto (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2.  Clique na página de propriedades **Compilar**.  
  
3.  Clique no botão **Avançado**.  
  
4.  Modifique a propriedade **Procurar estouro/estouro negativo aritmético**.  
  
 Para acessar programaticamente essa opção do compilador, confira <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.  
  
## <a name="example"></a>Exemplo  
 O comando a seguir compila `t2.cs`. O uso de `-checked` no comando especifica que qualquer instrução de aritmética de inteiros no arquivo que não está no escopo de uma palavra-chave `checked` ou `unchecked` e que resulta em um valor fora do intervalo do tipo de dados, causa uma exceção em tempo de execução.  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)  
