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
ms.openlocfilehash: 4df4e74fc13c922f51f5b74c3c152bdea28b4431
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005203"
---
# <a name="-rootnamespace"></a>-rootnamespace
Especifica um namespace para todas as declarações de tipo.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`namespace`|O nome do namespace no qual incluir todas as declarações de tipo para o projeto atual.|  
  
## <a name="remarks"></a>Comentários  
 Se você usar o arquivo executável do Visual Studio (devenv. exe) para compilar um projeto criado no ambiente de desenvolvimento integrado do Visual Studio, use `-rootnamespace` para especificar o valor da propriedade <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A>. Consulte [Opções de linha de comando do devenv](/visualstudio/ide/reference/devenv-command-line-switches) para obter mais informações.  
  
 Use o desmontador Common Language Runtime MSIL (`Ildasm.exe`) para exibir os nomes de namespace em seu arquivo de saída.  
  
|Para Set-RootNamespace no ambiente de desenvolvimento integrado do Visual Studio|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**. <br />2.  Clique na guia **Aplicativo**.<br />3.  Modifique o valor na caixa **namespace raiz** .|  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `In.vb` e inclui todas as declarações de tipo no namespace `mynamespace`.  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Ildasm.exe (IL Disassembler)](../../../framework/tools/ildasm-exe-il-disassembler.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
