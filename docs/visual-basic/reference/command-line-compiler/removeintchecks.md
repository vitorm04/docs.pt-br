---
title: -removeintchecks
ms.date: 03/13/2018
f1_keywords:
- removeintchecks
- -removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
ms.openlocfilehash: c086a031d5cef4563a6769e7683dcb1110b8fe49
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58822720"
---
# <a name="-removeintchecks"></a>-removeintchecks
Ativa o erro de estouro para operações de inteiros ou desativar a verificação.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`+` &#124; `-`|Opcional. O `-removeintchecks-` opção faz com que o compilador verifique todos os cálculos de inteiro para erros de estouro. O padrão é `-removeintchecks-`.<br /><br /> Especificando `-removeintchecks` ou `-removeintchecks+` impede a verificação de erros e pode fazer cálculos de inteiro mais rápidos. No entanto, sem verificação de erro, e se as capacidades de tipo de dados são estouradas, resultados incorretos podem ser armazenados sem gerar um erro.|  
  
|Definir - removeintchecks no ambiente de desenvolvimento integrado do Visual Studio|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**. <br />2.  Clique na guia **Compilar**.<br />3.  Clique no botão **Avançado**.<br />4.  Modificar o valor da **remover verificações de estouro de inteiro** caixa.|  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `Test.vb` e desativa a verificação de erro de estouro de inteiro.  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
