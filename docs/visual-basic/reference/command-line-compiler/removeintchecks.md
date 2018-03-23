---
title: -removeintchecks
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- removeintchecks
- -removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25a14ffaca6e61c6e3306f8ff58de441e2ba2ade
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="-removeintchecks"></a>-removeintchecks
Ativa para operações de inteiro ou desativar a verificação de erro de estouro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`+` &#124; `-`|Opcional. O `-removeintchecks-` opção faz com que o compilador verificar se todos os cálculos de inteiros para erros de estouro. O padrão é `-removeintchecks-`.<br /><br /> Especificando `-removeintchecks` ou `-removeintchecks+` impede a verificação de erro e pode fazer os cálculos de inteiros mais rápidos. No entanto, sem a verificação de erros, e se as capacidades de tipo de dados são estourou, resultados incorretos podem ser armazenados sem gerar um erro.|  
  
|Para definir - removeintchecks no ambiente de desenvolvimento integrado do Visual Studio|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**. <br />2.  Clique na guia **Compilar**.<br />3.  Clique no botão **Avançado**.<br />4.  Modificar o valor da **remover verificações de estouro de inteiro** caixa.|  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `Test.vb` e desativa a verificação de erro de estouro de inteiro.  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
