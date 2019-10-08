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
ms.openlocfilehash: bea6ca24ea6da9000267e754d52fe0ca152f7d7f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005234"
---
# <a name="-removeintchecks"></a>-removeintchecks
Ativa a verificação de erros de estouro para operações de inteiros.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`+` &#124; `-`|Opcional. A opção `-removeintchecks-` faz com que o compilador Verifique todos os cálculos de inteiro para erros de estouro. O padrão é `-removeintchecks-`.<br /><br /> Especificar `-removeintchecks` ou `-removeintchecks+` impede a verificação de erros e pode fazer cálculos de números inteiros mais rapidamente. No entanto, sem a verificação de erros e se as capacidades de tipo de dados estouram, os resultados incorretos podem ser armazenados sem gerar um erro.|  
  
|Para Set-removeintchecks no ambiente de desenvolvimento integrado do Visual Studio|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**. <br />2.  Clique na guia **Compilar**.<br />3.  Clique no botão **Avançado**.<br />4.  Modifique o valor da caixa de **verificações remover estouro de inteiro** .|  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `Test.vb` e desativa a verificação de erro de estouro de inteiros.  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
