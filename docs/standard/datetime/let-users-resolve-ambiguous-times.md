---
title: "Como permitir que os usuários resolvam horários ambíguos"
description: "Como permitir que os usuários resolvam horários ambíguos"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: d6858a5c-02ab-4367-9e08-fa22c051c38d
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: ede8d021a4f524cf37f7ad00b6aed89d1b1729f8
ms.contentlocale: pt-br
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-let-users-resolve-ambiguous-times"></a><span data-ttu-id="21d00-104">Como permitir que os usuários resolvam horários ambíguos</span><span class="sxs-lookup"><span data-stu-id="21d00-104">How to: let users resolve ambiguous times</span></span>

<span data-ttu-id="21d00-105">Um horário ambíguo é um horário que aponta para mais de um UTC (Tempo Universal Coordenado).</span><span class="sxs-lookup"><span data-stu-id="21d00-105">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="21d00-106">Ocorre quando o horário do relógio é atrasado, como durante a transição do horário de verão de um fuso horário para seu horário padrão.</span><span class="sxs-lookup"><span data-stu-id="21d00-106">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="21d00-107">Ao processar um horário ambíguo, você pode executar uma das seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="21d00-107">When handling an ambiguous time, you can do one of the following:</span></span>

* <span data-ttu-id="21d00-108">Se o horário ambíguo for um item de dados inserido pelo usuário, você pode deixar que o usuário resolva a ambiguidade.</span><span class="sxs-lookup"><span data-stu-id="21d00-108">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

* <span data-ttu-id="21d00-109">Faça uma suposição de como o tempo aponta para o UTC.</span><span class="sxs-lookup"><span data-stu-id="21d00-109">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="21d00-110">Por exemplo, você pode supor que um horário ambíguo é sempre expresso no horário padrão do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="21d00-110">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

<span data-ttu-id="21d00-111">Este artigo mostra como permitir que um usuário resolva um horário ambíguo.</span><span class="sxs-lookup"><span data-stu-id="21d00-111">This article shows how to let a user resolve an ambiguous time.</span></span>

## <a name="to-let-a-user-resolve-an-ambiguous-time"></a><span data-ttu-id="21d00-112">Permitir que o usuário resolva um horário ambíguo</span><span class="sxs-lookup"><span data-stu-id="21d00-112">To let a user resolve an ambiguous time</span></span>

1. <span data-ttu-id="21d00-113">Obtenha a entrada de data e hora do usuário.</span><span class="sxs-lookup"><span data-stu-id="21d00-113">Get the date and time input by the user.</span></span>

2. <span data-ttu-id="21d00-114">Chame o método [IsAmbiguousTime(DateTime)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTime)) ou [IsAmbiguousTime(DateTimeOffset)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTimeOffset)) para determinar se o horário é ambíguo.</span><span class="sxs-lookup"><span data-stu-id="21d00-114">Call the [IsAmbiguousTime(DateTime)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTime)) or [IsAmbiguousTime(DateTimeOffset)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTimeOffset)) method to determine whether the time is ambiguous.</span></span>

3. <span data-ttu-id="21d00-115">Permita que o usuário selecione o deslocamento desejado.</span><span class="sxs-lookup"><span data-stu-id="21d00-115">Let the user select the desired offset.</span></span>

4. <span data-ttu-id="21d00-116">Obtenha a data e hora de UTC subtraindo o deslocamento selecionado pelo usuário do horário local.</span><span class="sxs-lookup"><span data-stu-id="21d00-116">Get the UTC date and time by subtracting the offset selected by the user from the local time.</span></span>

5. <span data-ttu-id="21d00-117">Chame o método `static` (`Shared` no Visual Basic ) [SpecifyKind](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) para definir a propriedade [Kind](xref:System.DateTime.Kind) do valor de data e hora do UTC como [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).</span><span class="sxs-lookup"><span data-stu-id="21d00-117">Call the `static` (`Shared` in Visual Basic ) [SpecifyKind](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) method to set the UTC date and time value's [Kind](xref:System.DateTime.Kind) property to [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).</span></span>

## <a name="example"></a><span data-ttu-id="21d00-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="21d00-118">Example</span></span>

<span data-ttu-id="21d00-119">O exemplo a seguir solicita que o usuário insira uma data e hora e, se ela for ambígua, permite que o usuário selecione o horário UTC para o qual o horário ambíguo aponta.</span><span class="sxs-lookup"><span data-stu-id="21d00-119">The following example prompts the user to enter a date and time and, if it is ambiguous, lets the user select the UTC time that the ambiguous time maps to.</span></span> <span data-ttu-id="21d00-120">O exemplo usa um objeto [DateTime](xref:System.DateTime); você pode substituir um [DateTimeOffset](xref:System.DateTimeOffset) se desejar.</span><span class="sxs-lookup"><span data-stu-id="21d00-120">The example uses a [DateTime](xref:System.DateTime) object; you can substitute a [DateTimeOffset](xref:System.DateTimeOffset) object if desired.</span></span>

```csharp
private void GetUserDateInput()
{
   // Get date and time from user
   DateTime inputDate = GetUserDateTime();
   DateTime utcDate;

   // Exit if date has no significant value
   if (inputDate == DateTime.MinValue) return;

   if (TimeZoneInfo.Local.IsAmbiguousTime(inputDate))
   {
      Console.WriteLine("The date you've entered is ambiguous.");
      Console.WriteLine("Please select the correct offset from Universal Coordinated Time:");
      TimeSpan[] offsets = TimeZoneInfo.Local.GetAmbiguousTimeOffsets(inputDate);
      for (int ctr = 0; ctr < offsets.Length; ctr++)
      {
         Console.WriteLine("{0}.) {1} hours, {2} minutes", ctr, offsets[ctr].Hours, offsets[ctr].Minutes);
      }
      Console.Write("> ");
      int selection = Convert.ToInt32(Console.ReadLine());

      // Convert local time to UTC, and set Kind property to DateTimeKind.Utc
      utcDate = DateTime.SpecifyKind(inputDate - offsets[selection], DateTimeKind.Utc);

      Console.WriteLine("{0} local time corresponds to {1} {2}.", inputDate, utcDate, utcDate.Kind.ToString());
   }
   else
   {
      utcDate = inputDate.ToUniversalTime();
      Console.WriteLine("{0} local time corresponds to {1} {2}.", inputDate, utcDate, utcDate.Kind.ToString());    
   }
}

private DateTime GetUserDateTime() 
{
   bool exitFlag = false;             // flag to exit loop if date is valid
   string dateString;  
   DateTime inputDate = DateTime.MinValue;

   Console.Write("Enter a local date and time: ");
   while (! exitFlag)
   {
      dateString = Console.ReadLine();
      if (dateString.ToUpper() == "E")
         exitFlag = true;

      if (DateTime.TryParse(dateString, out inputDate))
         exitFlag = true;
      else
         Console.Write("Enter a valid date and time, or enter 'e' to exit: ");
   }

   return inputDate;        
}
```

```vb
Private Sub GetUserDateInput()
   ' Get date and time from user
   Dim inputDate As Date = GetUserDateTime()
   Dim utcDate As Date

   ' Exit if date has no significant value
   If inputDate = Date.MinValue Then Exit Sub

   If TimeZoneInfo.Local.IsAmbiguousTime(inputDate) Then
      Console.WriteLine("The date you've entered is ambiguous.")
      Console.WriteLine("Please select the correct offset from Universal Coordinated Time:")
      Dim offsets() As TimeSpan = TimeZoneInfo.Local.GetAmbiguousTimeOffsets(inputDate)
      For ctr As Integer = 0 to offsets.Length - 1
         Dim zoneDescription As String
         If offsets(ctr).Equals(TimeZoneInfo.Local.BaseUtcOffset) Then 
            zoneDescription = TimeZoneInfo.Local.StandardName
         Else
            zoneDescription = TimeZoneInfo.Local.DaylightName
         End If
         Console.WriteLine("{0}.) {1} hours, {2} minutes ({3})", _
                           ctr, offsets(ctr).Hours, offsets(ctr).Minutes, zoneDescription)
      Next         
      Console.Write("> ")
      Dim selection As Integer = CInt(Console.ReadLine())

      ' Convert local time to UTC, and set Kind property to DateTimeKind.Utc
      utcDate = Date.SpecifyKind(inputDate - offsets(selection), DateTimeKind.Utc)

      Console.WriteLine("{0} local time corresponds to {1} {2}.", inputDate, utcDate, utcDate.Kind.ToString())
   Else
      utcDate = inputDate.ToUniversalTime()
      Console.WriteLine("{0} local time corresponds to {1} {2}.", inputDate, utcDate, utcDate.Kind.ToString())    
   End If
End Sub

Private Function GetUserDateTime() As Date
   Dim exitFlag As Boolean = False            ' flag to exit loop if date is valid
   Dim dateString As String 
   Dim inputDate As Date = Date.MinValue

   Console.Write("Enter a local date and time: ")
   Do While Not exitFlag
      dateString = Console.ReadLine()
      If dateString.ToUpper = "E" Then exitFlag = True
      If Date.TryParse(dateString, inputDate) Then
         exitFlag = true
      Else   
         Console.Write("Enter a valid date and time, or enter 'e' to exit: ")
      End If
   Loop

   Return inputDate        
End Function
```

<span data-ttu-id="21d00-121">O núcleo do código de exemplo usa uma matriz de objetos [TimeSpan](xref:System.TimeSpan) para indicar possíveis deslocamentos de horário ambíguo do UTC.</span><span class="sxs-lookup"><span data-stu-id="21d00-121">The core of the example code uses an array of [TimeSpan](xref:System.TimeSpan) objects to indicate possible offsets of the ambiguous time from UTC.</span></span> <span data-ttu-id="21d00-122">No entanto, esses deslocamentos provavelmente não serão significativos para o usuário.</span><span class="sxs-lookup"><span data-stu-id="21d00-122">However, these offsets are unlikely to be meaningful to the user.</span></span> <span data-ttu-id="21d00-123">Para esclarecer o significado dos deslocamentos, o código também observa se um deslocamento representa o horário padrão do fuso horário local ou seu horário de verão.</span><span class="sxs-lookup"><span data-stu-id="21d00-123">To clarify the meaning of the offsets, the code also notes whether an offset represents the local time zone's standard time or its daylight saving time.</span></span> <span data-ttu-id="21d00-124">O código determina qual horário é padrão e qual é o de verão comparando o deslocamento com o valor da propriedade [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset).</span><span class="sxs-lookup"><span data-stu-id="21d00-124">The code determines which time is standard and which time is daylight by comparing the offset with the value of the [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) property.</span></span> <span data-ttu-id="21d00-125">Essa propriedade indica a diferença entre o UTC e o horário padrão do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="21d00-125">This property indicates the difference between the UTC and the time zone's standard time.</span></span>

<span data-ttu-id="21d00-126">Neste exemplo, todas as referências ao fuso horário local são feitas através da propriedade [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local); o fuso horário local nunca é atribuído a uma variável de objeto.</span><span class="sxs-lookup"><span data-stu-id="21d00-126">In this example, all references to the local time zone are made through the [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="21d00-127">Essa é uma prática recomendada porque outra chamada poderia limpar os dados em cache e invalidar todos os objetos aos quais o fuso horário local é atribuído.</span><span class="sxs-lookup"><span data-stu-id="21d00-127">This is a recommended practice because another call could clear the cached data and invalidate any objects that the local time zone is assigned to.</span></span>

## <a name="see-also"></a><span data-ttu-id="21d00-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21d00-128">See Also</span></span>

[<span data-ttu-id="21d00-129">Datas, horas e fusos horários</span><span class="sxs-lookup"><span data-stu-id="21d00-129">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="21d00-130">Como resolver horários ambíguos</span><span class="sxs-lookup"><span data-stu-id="21d00-130">How to: resolve ambiguous times</span></span>](resolve-ambiguous-times.md)


