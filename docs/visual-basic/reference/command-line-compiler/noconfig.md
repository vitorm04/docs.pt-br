---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: b707899c845b6b08e008fe229497f682c930044a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65588853"
---
# <a name="-noconfig"></a>-noconfig
Especifica que o compilador deve referenciar os assemblies do .NET Framework usados ou importar automaticamente o `System` e `Microsoft.VisualBasic` namespaces.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-noconfig  
```  
  
## <a name="remarks"></a>Comentários  
 O `-noconfig` opção informa o compilador não deve compilar com o arquivo Vbc. rsp, localizado no mesmo diretório que o arquivo Vbc.exe. O arquivo Vbc. rsp referencia assemblies do .NET Framework comumente usados e importa o `System` e `Microsoft.VisualBasic` namespaces. O compilador implicitamente referencia o assembly System. dll, a menos que o `-nostdlib` opção for especificada. O `-nostdlib` opção informa o compilador não deve compilar com Vbc ou automaticamente fazer referência ao assembly System. dll.  
  
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
