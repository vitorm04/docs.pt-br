---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 19a70e500f6b75fd003bdb798f242cddb3926935
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964359"
---
# <a name="-nostdlib-visual-basic"></a>-nostdlib (Visual Basic)
Faz com que o compilador não referencie automaticamente as bibliotecas padrão.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-nostdlib  
```  
  
## <a name="remarks"></a>Comentários  
 A `-nostdlib` opção remove a referência automática para o assembly System. dll e impede que o compilador Leia o arquivo Vbc. rsp. O arquivo Vbc. rsp, localizado no mesmo diretório que o arquivo Vbc. exe, faz referência aos assemblies de .NET Framework usados com frequência e importa os `System` namespaces e `Microsoft.VisualBasic` .  
  
> [!NOTE]
> Os assemblies mscorlib. dll e Microsoft. VisualBasic. dll são sempre referenciados.  
  
> [!NOTE]
> A `-nostdlib` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ela está disponível somente durante a compilação na linha de comando.  
  
## <a name="example"></a>Exemplo  
 O código a seguir é compilado `T2.vb` sem referenciar as bibliotecas padrão. Você deve definir a `_MYTYPE` constante de compilação condicional para a cadeia de caracteres "Empty" para `My` remover o objeto.  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>Consulte também

- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Personalizando quais objetos estão disponíveis em My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
