---
title: -/noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: bce2d98a8915e80cdecd7b67029b0c872cf70140
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="-noconfig"></a>-/noconfig
Especifica que o compilador não deve automaticamente referenciar comumente usados [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies ou importação de `System` e `Microsoft.VisualBasic` namespaces.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-noconfig  
```  
  
## <a name="remarks"></a>Comentários  
 O `-noconfig` opção informa ao compilador para não compilar com o arquivo Vbc.rsp, que está localizado no mesmo diretório que o arquivo Vbc.exe. O arquivo Vbc.rsp referencia comumente usados [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies e importa o `System` e `Microsoft.VisualBasic` namespaces. O compilador implicitamente referencia o assembly System. dll, a menos que o `-nostdlib` opção é especificada. O `-nostdlib` opção informa ao compilador para não compilar com Vbc ou referenciar automaticamente o assembly System. dll.  
  
> [!NOTE]
>  Os assemblies mscorlib. dll e Microsoft.VisualBasic.dll são sempre referenciados.  
  
 Você pode modificar o arquivo Vbc.rsp para especificar opções adicionais do compilador que devem ser incluídas em cada compilação Vbc.exe (exceto quando o `-noconfig` opção). Para obter mais informações, confira [@ (Especificar de arquivo de resposta)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).  
  
 O compilador processa as opções passadas para o `vbc` último comando. Portanto, qualquer opção na linha de comando substitui a configuração da mesma opção no arquivo Vbc.  
  
> [!NOTE]
>  O `-noconfig` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível somente quando estiver compilando na linha de comando.  
  
## <a name="see-also"></a>Consulte também  
 [-/nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md)  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Em (Especificar arquivo de resposta)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)  
 [-referência (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
