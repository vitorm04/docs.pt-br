---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: dc4c0336c8a67a1b4e70f71ba5f5406da1fbb2ff
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972383"
---
# <a name="-moduleassemblyname"></a>-moduleassemblyname
Especifica o nome do assembly do qual esse módulo fará parte.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`assembly_name`|O nome do assembly do qual este módulo fará parte.|  
  
## <a name="remarks"></a>Comentários  
 O compilador processará `-moduleassemblyname` a opção somente se `-target:module` a opção tiver sido especificada. Isso faz com que o compilador crie um módulo. O módulo criado pelo compilador é válido somente para o assembly especificado com a `-moduleassemblyname` opção. Se você posicionar o módulo em um assembly diferente, ocorrerão erros de tempo de execução.  
  
 A `-moduleassemblyname` opção é necessária somente quando as seguintes opções são verdadeiras:  
  
- Um tipo de dados no módulo precisa de acesso a `Friend` um tipo em um assembly referenciado.  
  
- O assembly referenciado concedeu acesso de assembly Friend ao assembly no qual o módulo será compilado.  
  
 Para obter mais informações sobre como criar um módulo, consulte [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md). Para obter mais informações sobre assemblies Friend, consulte [Friend Assemblies](../../../standard/assembly/friend.md).  
  
> [!NOTE]
> A `-moduleassemblyname` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ela está disponível somente quando você compila a partir de um prompt de comando.  
  
## <a name="see-also"></a>Consulte também

- [Como: Criar um assembly de vários arquivos](../../../framework/app-domains/build-multifile-assembly.md)
- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-main](../../../visual-basic/reference/command-line-compiler/main.md)
- [-referência (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [Assemblies no .NET](../../../standard/assembly/index.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Assemblies Amigáveis](../../../standard/assembly/friend.md)
