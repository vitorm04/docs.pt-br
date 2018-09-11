---
title: -rootnamespace
ms.date: 03/13/2018
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
ms.openlocfilehash: 13bce09ca9fd1ae9ebb919a9245d8ccf87fbde1d
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44368738"
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
|`namespace`|O nome do namespace no qual Circunscrever todas as declarações de tipo para o projeto atual.|  
  
## <a name="remarks"></a>Comentários  
 Se você usar o arquivo executável (Devenv.exe) do Visual Studio para compilar um projeto criado no ambiente de desenvolvimento integrado do Visual Studio, use `-rootnamespace` para especificar o valor da <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> propriedade. Ver [opções de linha de comando Devenv](/visualstudio/ide/reference/devenv-command-line-switches) para obter mais informações.  
  
 Use o common language runtime MSIL Disassembler (`Ildasm.exe`) para exibir os nomes de namespace em seu arquivo de saída.  
  
|Definir - rootnamespace no ambiente de desenvolvimento integrado do Visual Studio|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**. <br />2.  Clique na guia **Aplicativo**.<br />3.  Modificar o valor de **Namespace de raiz** caixa.|  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `In.vb` e inclui todas as declarações de tipo no namespace `mynamespace`.  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
- [Ildasm.exe (IL Disassembler)](../../../framework/tools/ildasm-exe-il-disassembler.md)  
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
