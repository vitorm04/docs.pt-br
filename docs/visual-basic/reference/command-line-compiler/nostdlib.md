---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3764409f13a00f6d8a050bfbdd0f59e537a5ded3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43456286"
---
# <a name="-nostdlib-visual-basic"></a>-nostdlib (Visual Basic)
Faz com que o compilador não referencie automaticamente as bibliotecas padrão.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-nostdlib  
```  
  
## <a name="remarks"></a>Comentários  
 O `-nostdlib` opção remove a referência automática para o assembly System. dll e impede que o compilador lendo o arquivo Vbc. rsp. O arquivo Vbc. rsp, que está localizado no mesmo diretório que o arquivo Vbc.exe, faz referência os comumente usados [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies e importações a `System` e `Microsoft.VisualBasic` namespaces.  
  
> [!NOTE]
>  Os assemblies de mscorlib. dll e VisualBasic são sempre referenciados.  
  
> [!NOTE]
>  O `-nostdlib` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente durante a compilação da linha de comando.  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `T2.vb` sem fazer referência às bibliotecas padrão. Você deve definir a `_MYTYPE` constante de compilação condicional para a cadeia de caracteres "Vazio" para remover o `My` objeto.  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Personalizando quais objetos estão disponíveis em My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
