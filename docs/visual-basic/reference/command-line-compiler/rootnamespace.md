---
title: /RootNamespace | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /rootnamespace
- rootnamespace
dev_langs:
- VB
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
caps.latest.revision: 13
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7b261efeb829a6c0b035d7364c63074412a91c7f
ms.lasthandoff: 03/13/2017

---
# <a name="rootnamespace"></a>/rootnamespace
Especifica um namespace para todas as declarações de tipo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/rootnamespace:namespace  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`namespace`|O nome do namespace no qual colocar todas as declarações de tipo para o projeto atual.|  
  
## <a name="remarks"></a>Comentários  
 Se você usar o arquivo executável do Visual Studio (Devenv.exe) para compilar um projeto criado no ambiente de desenvolvimento integrado do Visual Studio, use `/rootnamespace` para especificar o valor de <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A>propriedade.</xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> Consulte [opções de linha de comando Devenv](https://docs.microsoft.com/visualstudio/ide/reference/devenv-command-line-switches) para obter mais informações.  
  
 Use o common language runtime MSIL Disassembler (eu`ldasm.exe`) para exibir os nomes de namespace em seu arquivo de saída.  
  
|Para definir /rootnamespace no Visual Studio ambiente de desenvolvimento integrado|  
|---|  
|1.  Tenha um projeto selecionado no **Solution Explorer**. No menu **Projeto**, clique em **Propriedades**. Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Clique o **aplicativo** guia.<br />3.  Modificar o valor de **Namespace raiz** caixa.|  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `In.vb` e inclui todas as declarações de tipo no namespace `mynamespace`.  
  
```  
vbc /rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1)   
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
