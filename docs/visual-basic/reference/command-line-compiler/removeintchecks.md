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
ms.openlocfilehash: ce1f24f25ea58cb6ddc2f5c582b6103d8f18d922
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085159"
---
# <a name="-removeintchecks"></a>-removeintchecks

Ativa a verificação de erros de estouro para operações de inteiros.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a>Argumentos  
  
|Termo|Definição|  
|---|---|  
|`+` &#124; `-`|Opcional. A `-removeintchecks-` opção faz com que o compilador Verifique todos os cálculos de inteiro para erros de estouro. O padrão é `-removeintchecks-`.<br /><br /> Especificar `-removeintchecks` ou `-removeintchecks+` impedir a verificação de erros e pode fazer cálculos de números inteiros mais rapidamente. No entanto, sem a verificação de erros e se as capacidades de tipo de dados estouram, os resultados incorretos podem ser armazenados sem gerar um erro.|  
  
|Para Set-removeintchecks no ambiente de desenvolvimento integrado do Visual Studio|  
|---|  
|1. ter um projeto selecionado em **Gerenciador de soluções**. No menu **Projeto** , clique em **Propriedades**. <br />2. Clique na guia **Compilar** .<br />3. Clique no botão **avançado** .<br />4. modifique o valor da caixa de **verificações remover estouro de inteiro** .|  
  
## <a name="example"></a>Exemplo  

 O código a seguir compila `Test.vb` e desativa a verificação de erro de estouro de inteiros.  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>Confira também

- [Compilador de linha de comando do Visual Basic](index.md)
- [Linhas de Comando de Compilação de Exemplo](sample-compilation-command-lines.md)
