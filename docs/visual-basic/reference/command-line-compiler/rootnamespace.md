---
title: -rootnamespace
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45dce293549674e7e6aac2714e1a7a569719c597
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="-rootnamespace"></a>-rootnamespace
Especifica um namespace para todas as declarações de tipo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`namespace`|O nome do namespace no qual colocar todas as declarações de tipo para o projeto atual.|  
  
## <a name="remarks"></a>Comentários  
 Se você usar o arquivo executável do Visual Studio (Devenv.exe) para compilar um projeto criado no ambiente de desenvolvimento integrado do Visual Studio, use `-rootnamespace` para especificar o valor da <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> propriedade. Consulte [opções de linha de comando Devenv](/visualstudio/ide/reference/devenv-command-line-switches) para obter mais informações.  
  
 Use o common language runtime MSIL Disassembler (`Ildasm.exe`) para exibir os nomes de namespace em seu arquivo de saída.  
  
|Para definir - rootnamespace no ambiente de desenvolvimento integrado do Visual Studio|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**. <br />2.  Clique na guia **Aplicativo**.<br />3.  Modificar o valor de **Namespace raiz** caixa.|  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `In.vb` e inclui todas as declarações de tipo no namespace `mynamespace`.  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
