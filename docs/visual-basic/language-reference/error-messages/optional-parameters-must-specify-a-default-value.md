---
title: Parâmetros opcionais devem especificar um valor padrão
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: eb782b2fa1fb73c7407b57a0942e5eebb30474ff
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040935"
---
# <a name="optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="5106e-102">Parâmetros opcionais devem especificar um valor padrão</span><span class="sxs-lookup"><span data-stu-id="5106e-102">Optional parameters must specify a default value</span></span>

<span data-ttu-id="5106e-103">Parâmetros opcionais devem fornecer valores padrão que podem ser usados se nenhum parâmetro for fornecido por um procedimento de chamada.</span><span class="sxs-lookup"><span data-stu-id="5106e-103">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>

<span data-ttu-id="5106e-104">**ID do erro:** BC30812</span><span class="sxs-lookup"><span data-stu-id="5106e-104">**Error ID:** BC30812</span></span>

## <a name="example"></a><span data-ttu-id="5106e-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5106e-105">Example</span></span>

<span data-ttu-id="5106e-106">O exemplo a seguir gera BC30812:</span><span class="sxs-lookup"><span data-stu-id="5106e-106">The following example generates BC30812:</span></span>

```vb
Sub Proc1(x As Integer, Optional y As String)
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="to-correct-this-error"></a><span data-ttu-id="5106e-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="5106e-107">To correct this error</span></span>

<span data-ttu-id="5106e-108">Especifique valores padrão para parâmetros opcionais:</span><span class="sxs-lookup"><span data-stu-id="5106e-108">Specify default values for optional parameters:</span></span>

```vb
Sub Proc1(x As Integer, Optional y As String = "Default Value")
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="see-also"></a><span data-ttu-id="5106e-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5106e-109">See also</span></span>

- [<span data-ttu-id="5106e-110">Opcional</span><span class="sxs-lookup"><span data-stu-id="5106e-110">Optional</span></span>](../modifiers/optional.md)
