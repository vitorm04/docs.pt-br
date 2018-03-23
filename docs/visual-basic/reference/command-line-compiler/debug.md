---
title: /debug (Visual Basic)
ms.date: 03/10/2018
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7430a3ac85a86ed5528af9ea830da530208749eb
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="-debug-visual-basic"></a>-a depuração (Visual Basic)
Faz com que o compilador gere informações de depuração e colocá-lo nos arquivos de saída.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-debug[+ | -]  
' -or-  
-debug:[full | pdbonly]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`+` &#124; `-`|Opcional. Especificando `+` ou `/debug` faz com que o compilador gerar informações de depuração e colocá-lo em um arquivo. PDB. Especificando `-` tem o mesmo efeito que não especificar `/debug`.|  
|`full` &#124; `pdbonly`|Opcional. Especifica o tipo de informações de depuração geradas pelo compilador. Se você não especificar `/debug:pdbonly`, o padrão é `full`, que permite anexar um depurador para o programa em execução. O `pdbonly` argumento permite a depuração de código-fonte quando o programa for iniciado no depurador, mas ele exibe o código de linguagem de assembly somente quando o programa em execução está anexado ao depurador.|  
  
## <a name="remarks"></a>Comentários  
 Use essa opção para criar builds de depuração. Se você não especificar `/debug`, `/debug+`, ou `/debug:full`, não será possível depurar o arquivo de saída do programa.  
  
 Por padrão, as informações de depuração não é emitida (`/debug-`). Para emitir informações de depuração, especifique `/debug` ou `/debug+`.  
  
 Para obter informações sobre como configurar o desempenho de depuração de um aplicativo, consulte [Facilitando a depuração de uma imagem](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).  
  
|Para definir - depurar no ambiente de desenvolvimento integrado do Visual Studio|  
|---|  
|1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**. <br />2.  Clique na guia **Compilar**.<br />3.  Clique em **Opções Avançadas de Compilação**.<br />4.  Modificar o valor de **gerar informações de depuração** caixa.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir coloca as informações de depuração no arquivo de saída `App.exe`.  
  
```  
vbc -debug -out:app.exe test.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
