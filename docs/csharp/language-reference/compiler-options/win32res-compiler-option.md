---
title: -win32res (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /win32res
helpviewer_keywords:
- win32res compiler option
- /win32res compiler option [C#]
- -win32res compiler option [C#]
- win32res compiler option [C#]
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
ms.openlocfilehash: 4026fcbd7dc2ef29c1e7ee01a0f37b3ff471b187
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322365"
---
# <a name="-win32res-c-compiler-options"></a>-win32res (opções do compilador C#)
A opção **-win32res** insere um recurso do Win32 no arquivo de saída.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 O arquivo de recurso que você deseja adicionar ao seu arquivo de saída.  
  
## <a name="remarks"></a>Comentários  
 Um arquivo de recurso do Win32 pode ser criado com o [Compilador de Recursos](../../language-reference/compiler-options/resource-compiler-option.md). O Compilador de Recursos é invocado quando você compila um programa do Visual C++; um arquivo .res é criado com base no arquivo .rc.  
  
 Um recurso do Win32 pode conter informações de versão ou de bitmap (ícone) que ajudariam a identificar seu aplicativo no Explorador de Arquivos. Se você não especificar a **-win32res**, o compilador gerará informações de versão com base na versão do assembly.  
  
 Consulte [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (para referenciar) ou [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (para anexar) um arquivo de recurso do .NET Framework.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1. Abra a página **Propriedades** do projeto.  
  
2. Clique na página de propriedades do **Aplicativo**.  
  
3. Clique no botão **Arquivo de Recurso** e escolha um arquivo usando a caixa de combinação.  
  
## <a name="example"></a>Exemplo  
 Compilar `in.cs` e anexar um arquivo de recurso do Win32 `rf.res` para produzir `in.exe`:  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a>Consulte também

- [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)
- [Gerenciando propriedades de solução e projeto](/visualstudio/ide/managing-project-and-solution-properties)
