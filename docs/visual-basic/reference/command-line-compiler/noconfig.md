---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: 44bc619c489fdff36f0b595f7d8934689b859adb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789019"
---
# <a name="-noconfig"></a>-noconfig
Especifica que o compilador não deve automaticamente referenciar os comumente usados [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies ou importar os `System` e `Microsoft.VisualBasic` namespaces.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-noconfig  
```  
  
## <a name="remarks"></a>Comentários  
 O `-noconfig` opção informa o compilador não deve compilar com o arquivo Vbc. rsp, localizado no mesmo diretório que o arquivo Vbc.exe. O arquivo Vbc. rsp referencia os comumente usados [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies e importações a `System` e `Microsoft.VisualBasic` namespaces. O compilador implicitamente referencia o assembly System. dll, a menos que o `-nostdlib` opção for especificada. O `-nostdlib` opção informa o compilador não deve compilar com Vbc ou automaticamente fazer referência ao assembly System. dll.  
  
> [!NOTE]
>  Os assemblies de mscorlib. dll e VisualBasic são sempre referenciados.  
  
 Você pode modificar o arquivo Vbc. exe para especificar opções do compilador adicionais que devem ser incluídas em cada compilação Vbc.exe (exceto quando o `-noconfig` opção). Para obter mais informações, confira [@ (Especificar de arquivo de resposta)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).  
  
 O compilador processa as opções passadas para o `vbc` comando pela última vez. Portanto, qualquer opção na linha de comando substitui a configuração da mesma opção no arquivo Vbc.  
  
> [!NOTE]
>  O `-noconfig` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente durante a compilação da linha de comando.  
  
## <a name="see-also"></a>Consulte também

- [-nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md)
- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Em (Especificar arquivo de resposta)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)
- [-referência (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
