---
title: /removeintchecks
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- removeintchecks
- /removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 917977d8e5e12c231370ab3c956aca9d96e8a8a8
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="removeintchecks"></a>/removeintchecks
Ativa para operações de inteiro ou desativar a verificação de erro de estouro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`+` &#124; `-`|Opcional. O `/removeintchecks-` opção faz com que o compilador verificar se todos os cálculos de inteiros para erros de estouro. O padrão é `/removeintchecks-`.<br /><br /> Especificando `/removeintchecks` ou `/removeintchecks+` impede a verificação de erro e pode fazer os cálculos de inteiros mais rápidos. No entanto, sem a verificação de erros, e se as capacidades de tipo de dados são estourou, resultados incorretos podem ser armazenados sem gerar um erro.|  
  
|Para definir /removeintchecks no Visual Studio ambiente de desenvolvimento integrado|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**. <br />2.  Clique na guia **Compilar**.<br />3.  Clique no botão **Avançado**.<br />4.  Modificar o valor da **remover verificações de estouro de inteiro** caixa.|  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `Test.vb` e desativa a verificação de erro de estouro de inteiro.  
  
```  
vbc /removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
