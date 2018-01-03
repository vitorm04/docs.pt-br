---
title: /rootnamespace
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b02171b28034d676b7027e96c2c66e36be9ae604
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
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
 Se você usar o arquivo executável do Visual Studio (Devenv.exe) para compilar um projeto criado no ambiente de desenvolvimento integrado do Visual Studio, use `/rootnamespace` para especificar o valor da <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> propriedade. Consulte [opções de linha de comando Devenv](/visualstudio/ide/reference/devenv-command-line-switches) para obter mais informações.  
  
 Use o common language runtime MSIL Disassembler (`Ildasm.exe`) para exibir os nomes de namespace em seu arquivo de saída.  
  
|Para definir /rootnamespace no Visual Studio ambiente de desenvolvimento integrado|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**. <br />2.  Clique na guia **Aplicativo**.<br />3.  Modificar o valor de **Namespace raiz** caixa.|  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `In.vb` e inclui todas as declarações de tipo no namespace `mynamespace`.  
  
```  
vbc /rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
