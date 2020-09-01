---
description: -win32res (opções do compilador C#)
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
ms.openlocfilehash: c220c78a6d2c3109402a20f0de40fe9665d6c730
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89140809"
---
# <a name="-win32res-c-compiler-options"></a>-win32res (opções do compilador C#)
A opção **-win32res** insere um recurso do Win32 no arquivo de saída.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a>Argumentos  
 `filename`  
 O arquivo de recurso que você deseja adicionar ao seu arquivo de saída.  
  
## <a name="remarks"></a>Comentários  
 Um arquivo de recurso do Win32 pode ser criado com o [Compilador de Recursos](resource-compiler-option.md). O Compilador de Recursos é invocado quando você compila um programa do Visual C++; um arquivo .res é criado com base no arquivo .rc.  
  
 Um recurso do Win32 pode conter informações de versão ou de bitmap (ícone) que ajudariam a identificar seu aplicativo no Explorador de Arquivos. Se você não especificar a **-win32res**, o compilador gerará informações de versão com base na versão do assembly.  
  
 Consulte [-linkresource](./linkresource-compiler-option.md) (para referenciar) ou [-resource](./resource-compiler-option.md) (para anexar) um arquivo de recurso do .NET Framework.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1. Abra a página **Propriedades** do projeto.  
  
2. Clique na página de propriedades do **Aplicativo**.  
  
3. Clique no botão **Arquivo de Recurso** e escolha um arquivo usando a caixa de combinação.  
  
## <a name="example"></a>Exemplo  
 Compilar `in.cs` e anexar um arquivo de recurso do Win32 `rf.res` para produzir `in.exe`:  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a>Confira também

- [Opções do compilador C#](./index.md)
- [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
