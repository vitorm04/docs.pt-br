---
title: -win32resource
ms.date: 03/13/2018
f1_keywords:
- -win32resource
- win32resource
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
ms.openlocfilehash: 05dcaa18d799912d1b92685338a269a050db3f1a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54703478"
---
# <a name="-win32resource"></a>-win32resource
Insere um arquivo de recurso Win32 no arquivo de saída.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-win32resource:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 O nome do arquivo de recurso para adicionar ao seu arquivo de saída. Coloque o nome do arquivo entre aspas ("") se ele contiver um espaço.  
  
## <a name="remarks"></a>Comentários  
 Você pode criar um arquivo de recurso do Win32 com o compilador de recurso do Microsoft Windows (RC).  
  
 Um recurso do Win32 pode conter a versão ou informações de bitmap (ícone) que ajudam a identificar seu aplicativo no **Explorador de arquivos**. Se você não especificar `-win32resource`, o compilador gera informações de versão com base na versão do assembly. O `-win32resource` e `-win32icon` são mutuamente exclusivas.  
  
 Ver [- linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) a referência de uma [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] arquivo de recurso, ou [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) anexar um [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] arquivo de recurso.  
  
> [!NOTE]
>  O `-win32resource` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente durante a compilação da linha de comando.  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `In.vb` e anexa um arquivo de recurso do Win32, `Rf.res`:  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a>Consulte também
- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
