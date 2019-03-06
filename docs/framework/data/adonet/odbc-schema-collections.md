---
title: Coleções de esquema ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: ffe80120ceffbe29c0a117cf1194860c5782be8c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365900"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="e7409-102">Coleções de esquema ODBC</span><span class="sxs-lookup"><span data-stu-id="e7409-102">ODBC Schema Collections</span></span>

<span data-ttu-id="e7409-103">Esta seção discute o suporte de coleção de esquema para os drivers ODBC para Microsoft SQL Server, Oracle e Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="e7409-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>

## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="e7409-104">Driver ODBC do Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="e7409-104">Microsoft SQL Server ODBC Driver</span></span>

<span data-ttu-id="e7409-105">O Driver ODBC do Microsoft SQL Server suporta as seguintes coleções de esquema específico, além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="e7409-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="e7409-106">Tabelas</span><span class="sxs-lookup"><span data-stu-id="e7409-106">Tables</span></span>

- <span data-ttu-id="e7409-107">Índices</span><span class="sxs-lookup"><span data-stu-id="e7409-107">Indexes</span></span>

- <span data-ttu-id="e7409-108">Colunas</span><span class="sxs-lookup"><span data-stu-id="e7409-108">Columns</span></span>

- <span data-ttu-id="e7409-109">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="e7409-109">Procedures</span></span>

- <span data-ttu-id="e7409-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="e7409-110">ProcedureColumns</span></span>

- <span data-ttu-id="e7409-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e7409-111">ProcedureParameters</span></span>

- <span data-ttu-id="e7409-112">Exibições</span><span class="sxs-lookup"><span data-stu-id="e7409-112">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="e7409-113">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="e7409-113">Tables and Views</span></span>

|<span data-ttu-id="e7409-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e7409-114">ColumnName</span></span>|<span data-ttu-id="e7409-115">DataType</span><span class="sxs-lookup"><span data-stu-id="e7409-115">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e7409-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="e7409-116">TABLE_CAT</span></span>|<span data-ttu-id="e7409-117">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-117">String</span></span>|
|<span data-ttu-id="e7409-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="e7409-118">TABLE_SCHEM</span></span>|<span data-ttu-id="e7409-119">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-119">String</span></span>|
|<span data-ttu-id="e7409-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-120">TABLE_NAME</span></span>|<span data-ttu-id="e7409-121">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-121">String</span></span>|
|<span data-ttu-id="e7409-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e7409-122">TABLE_TYPE</span></span>|<span data-ttu-id="e7409-123">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-123">String</span></span>|
|<span data-ttu-id="e7409-124">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="e7409-124">REMARKS</span></span>|<span data-ttu-id="e7409-125">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-125">String</span></span>|

### <a name="indexes"></a><span data-ttu-id="e7409-126">Índices</span><span class="sxs-lookup"><span data-stu-id="e7409-126">Indexes</span></span>

|<span data-ttu-id="e7409-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e7409-127">ColumnName</span></span>|<span data-ttu-id="e7409-128">DataType</span><span class="sxs-lookup"><span data-stu-id="e7409-128">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e7409-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="e7409-129">TABLE_CAT</span></span>|<span data-ttu-id="e7409-130">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-130">String</span></span>|
|<span data-ttu-id="e7409-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="e7409-131">TABLE_SCHEM</span></span>|<span data-ttu-id="e7409-132">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-132">String</span></span>|
|<span data-ttu-id="e7409-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-133">TABLE_NAME</span></span>|<span data-ttu-id="e7409-134">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-134">String</span></span>|
|<span data-ttu-id="e7409-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="e7409-135">NON_UNIQUE</span></span>|<span data-ttu-id="e7409-136">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-136">Int16</span></span>|
|<span data-ttu-id="e7409-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e7409-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="e7409-138">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-138">String</span></span>|
|<span data-ttu-id="e7409-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-139">INDEX_NAME</span></span>|<span data-ttu-id="e7409-140">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-140">String</span></span>|
|<span data-ttu-id="e7409-141">TIPO</span><span class="sxs-lookup"><span data-stu-id="e7409-141">TYPE</span></span>|<span data-ttu-id="e7409-142">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-142">Int16</span></span>|
|<span data-ttu-id="e7409-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e7409-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="e7409-144">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-144">Int16</span></span>|
|<span data-ttu-id="e7409-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-145">COLUMN_NAME</span></span>|<span data-ttu-id="e7409-146">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-146">String</span></span>|
|<span data-ttu-id="e7409-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="e7409-147">ASC_OR_DESC</span></span>|<span data-ttu-id="e7409-148">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-148">String</span></span>|
|<span data-ttu-id="e7409-149">CARDINALIDADE</span><span class="sxs-lookup"><span data-stu-id="e7409-149">CARDINALITY</span></span>|<span data-ttu-id="e7409-150">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-150">Int32</span></span>|
|<span data-ttu-id="e7409-151">PÁGINAS</span><span class="sxs-lookup"><span data-stu-id="e7409-151">PAGES</span></span>|<span data-ttu-id="e7409-152">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-152">Int32</span></span>|
|<span data-ttu-id="e7409-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="e7409-153">FILTER_CONDITION</span></span>|<span data-ttu-id="e7409-154">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-154">String</span></span>|
|<span data-ttu-id="e7409-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e7409-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="e7409-156">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-156">String</span></span>|
|<span data-ttu-id="e7409-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e7409-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="e7409-158">Byte</span><span class="sxs-lookup"><span data-stu-id="e7409-158">Byte</span></span>|

### <a name="columns"></a><span data-ttu-id="e7409-159">Colunas</span><span class="sxs-lookup"><span data-stu-id="e7409-159">Columns</span></span>

|<span data-ttu-id="e7409-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e7409-160">ColumnName</span></span>|<span data-ttu-id="e7409-161">DataType</span><span class="sxs-lookup"><span data-stu-id="e7409-161">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e7409-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="e7409-162">TABLE_CAT</span></span>|<span data-ttu-id="e7409-163">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-163">String</span></span>|
|<span data-ttu-id="e7409-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="e7409-164">TABLE_SCHEM</span></span>|<span data-ttu-id="e7409-165">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-165">String</span></span>|
|<span data-ttu-id="e7409-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-166">TABLE_NAME</span></span>|<span data-ttu-id="e7409-167">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-167">String</span></span>|
|<span data-ttu-id="e7409-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-168">COLUMN_NAME</span></span>|<span data-ttu-id="e7409-169">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-169">String</span></span>|
|<span data-ttu-id="e7409-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e7409-170">DATA_TYPE</span></span>|<span data-ttu-id="e7409-171">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-171">Int16</span></span>|
|<span data-ttu-id="e7409-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-172">TYPE_NAME</span></span>|<span data-ttu-id="e7409-173">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-173">String</span></span>|
|<span data-ttu-id="e7409-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="e7409-174">COLUMN_SIZE</span></span>|<span data-ttu-id="e7409-175">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-175">Int32</span></span>|
|<span data-ttu-id="e7409-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e7409-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="e7409-177">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-177">Int32</span></span>|
|<span data-ttu-id="e7409-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="e7409-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="e7409-179">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-179">Int16</span></span>|
|<span data-ttu-id="e7409-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="e7409-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="e7409-181">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-181">Int16</span></span>|
|<span data-ttu-id="e7409-182">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="e7409-182">NULLABLE</span></span>|<span data-ttu-id="e7409-183">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-183">Int16</span></span>|
|<span data-ttu-id="e7409-184">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="e7409-184">REMARKS</span></span>|<span data-ttu-id="e7409-185">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-185">String</span></span>|
|<span data-ttu-id="e7409-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="e7409-186">COLUMN_DEF</span></span>|<span data-ttu-id="e7409-187">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-187">String</span></span>|
|<span data-ttu-id="e7409-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e7409-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="e7409-189">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-189">Int16</span></span>|
|<span data-ttu-id="e7409-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="e7409-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="e7409-191">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-191">Int16</span></span>|
|<span data-ttu-id="e7409-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e7409-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="e7409-193">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-193">Int32</span></span>|
|<span data-ttu-id="e7409-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e7409-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="e7409-195">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-195">Int32</span></span>|
|<span data-ttu-id="e7409-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e7409-196">IS_NULLABLE</span></span>|<span data-ttu-id="e7409-197">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-197">String</span></span>|
|<span data-ttu-id="e7409-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e7409-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="e7409-199">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-199">String</span></span>|
|<span data-ttu-id="e7409-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e7409-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="e7409-201">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-201">String</span></span>|
|<span data-ttu-id="e7409-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e7409-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="e7409-203">Byte</span><span class="sxs-lookup"><span data-stu-id="e7409-203">Byte</span></span>|

### <a name="procedures"></a><span data-ttu-id="e7409-204">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="e7409-204">Procedures</span></span>

|<span data-ttu-id="e7409-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e7409-205">ColumnName</span></span>|<span data-ttu-id="e7409-206">DataType</span><span class="sxs-lookup"><span data-stu-id="e7409-206">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e7409-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="e7409-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="e7409-208">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-208">String</span></span>|
|<span data-ttu-id="e7409-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="e7409-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="e7409-210">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-210">String</span></span>|
|<span data-ttu-id="e7409-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="e7409-212">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-212">String</span></span>|
|<span data-ttu-id="e7409-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="e7409-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="e7409-214">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-214">Int32</span></span>|
|<span data-ttu-id="e7409-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="e7409-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="e7409-216">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-216">Int32</span></span>|
|<span data-ttu-id="e7409-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="e7409-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="e7409-218">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-218">Int32</span></span>|
|<span data-ttu-id="e7409-219">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="e7409-219">REMARKS</span></span>|<span data-ttu-id="e7409-220">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-220">String</span></span>|
|<span data-ttu-id="e7409-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e7409-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="e7409-222">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-222">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="e7409-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="e7409-223">ProcedureColumns</span></span>

|<span data-ttu-id="e7409-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e7409-224">ColumnName</span></span>|<span data-ttu-id="e7409-225">DataType</span><span class="sxs-lookup"><span data-stu-id="e7409-225">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e7409-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="e7409-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="e7409-227">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-227">String</span></span>|
|<span data-ttu-id="e7409-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="e7409-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="e7409-229">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-229">String</span></span>|
|<span data-ttu-id="e7409-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="e7409-231">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-231">String</span></span>|
|<span data-ttu-id="e7409-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-232">COLUMN_NAME</span></span>|<span data-ttu-id="e7409-233">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-233">String</span></span>|
|<span data-ttu-id="e7409-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="e7409-234">COLUMN_TYPE</span></span>|<span data-ttu-id="e7409-235">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-235">Int16</span></span>|
|<span data-ttu-id="e7409-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e7409-236">DATA_TYPE</span></span>|<span data-ttu-id="e7409-237">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-237">Int16</span></span>|
|<span data-ttu-id="e7409-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-238">TYPE_NAME</span></span>|<span data-ttu-id="e7409-239">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-239">String</span></span>|
|<span data-ttu-id="e7409-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="e7409-240">COLUMN_SIZE</span></span>|<span data-ttu-id="e7409-241">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-241">Int32</span></span>|
|<span data-ttu-id="e7409-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e7409-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="e7409-243">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-243">Int32</span></span>|
|<span data-ttu-id="e7409-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="e7409-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="e7409-245">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-245">Int16</span></span>|
|<span data-ttu-id="e7409-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="e7409-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="e7409-247">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-247">Int16</span></span>|
|<span data-ttu-id="e7409-248">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="e7409-248">NULLABLE</span></span>|<span data-ttu-id="e7409-249">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-249">Int16</span></span>|
|<span data-ttu-id="e7409-250">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="e7409-250">REMARKS</span></span>|<span data-ttu-id="e7409-251">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-251">String</span></span>|
|<span data-ttu-id="e7409-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="e7409-252">COLUMN_DEF</span></span>|<span data-ttu-id="e7409-253">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-253">String</span></span>|
|<span data-ttu-id="e7409-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e7409-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="e7409-255">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-255">Int16</span></span>|
|<span data-ttu-id="e7409-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="e7409-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="e7409-257">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-257">Int16</span></span>|
|<span data-ttu-id="e7409-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e7409-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="e7409-259">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-259">Int32</span></span>|
|<span data-ttu-id="e7409-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e7409-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="e7409-261">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-261">Int32</span></span>|
|<span data-ttu-id="e7409-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e7409-262">IS_NULLABLE</span></span>|<span data-ttu-id="e7409-263">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-263">String</span></span>|
|<span data-ttu-id="e7409-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e7409-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="e7409-265">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-265">String</span></span>|
|<span data-ttu-id="e7409-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e7409-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="e7409-267">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-267">String</span></span>|
|<span data-ttu-id="e7409-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e7409-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="e7409-269">Byte</span><span class="sxs-lookup"><span data-stu-id="e7409-269">Byte</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="e7409-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e7409-270">ProcedureParameters</span></span>

|<span data-ttu-id="e7409-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e7409-271">ColumnName</span></span>|<span data-ttu-id="e7409-272">DataType</span><span class="sxs-lookup"><span data-stu-id="e7409-272">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e7409-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="e7409-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="e7409-274">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-274">String</span></span>|
|<span data-ttu-id="e7409-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="e7409-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="e7409-276">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-276">String</span></span>|
|<span data-ttu-id="e7409-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="e7409-278">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-278">String</span></span>|
|<span data-ttu-id="e7409-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-279">COLUMN_NAME</span></span>|<span data-ttu-id="e7409-280">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-280">String</span></span>|
|<span data-ttu-id="e7409-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="e7409-281">COLUMN_TYPE</span></span>|<span data-ttu-id="e7409-282">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-282">Int16</span></span>|
|<span data-ttu-id="e7409-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e7409-283">DATA_TYPE</span></span>|<span data-ttu-id="e7409-284">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-284">Int16</span></span>|
|<span data-ttu-id="e7409-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-285">TYPE_NAME</span></span>|<span data-ttu-id="e7409-286">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-286">String</span></span>|
|<span data-ttu-id="e7409-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="e7409-287">COLUMN_SIZE</span></span>|<span data-ttu-id="e7409-288">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-288">Int32</span></span>|
|<span data-ttu-id="e7409-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e7409-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="e7409-290">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-290">Int32</span></span>|
|<span data-ttu-id="e7409-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="e7409-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="e7409-292">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-292">Int16</span></span>|
|<span data-ttu-id="e7409-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="e7409-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="e7409-294">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-294">Int16</span></span>|
|<span data-ttu-id="e7409-295">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="e7409-295">NULLABLE</span></span>|<span data-ttu-id="e7409-296">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-296">Int16</span></span>|
|<span data-ttu-id="e7409-297">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="e7409-297">REMARKS</span></span>|<span data-ttu-id="e7409-298">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-298">String</span></span>|
|<span data-ttu-id="e7409-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="e7409-299">COLUMN_DEF</span></span>|<span data-ttu-id="e7409-300">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-300">String</span></span>|
|<span data-ttu-id="e7409-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e7409-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="e7409-302">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-302">Int16</span></span>|
|<span data-ttu-id="e7409-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="e7409-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="e7409-304">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-304">Int16</span></span>|
|<span data-ttu-id="e7409-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e7409-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="e7409-306">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-306">Int32</span></span>|
|<span data-ttu-id="e7409-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e7409-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="e7409-308">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-308">Int32</span></span>|
|<span data-ttu-id="e7409-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e7409-309">IS_NULLABLE</span></span>|<span data-ttu-id="e7409-310">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-310">String</span></span>|
|<span data-ttu-id="e7409-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e7409-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="e7409-312">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-312">String</span></span>|
|<span data-ttu-id="e7409-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e7409-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="e7409-314">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-314">String</span></span>|
|<span data-ttu-id="e7409-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e7409-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="e7409-316">Byte</span><span class="sxs-lookup"><span data-stu-id="e7409-316">Byte</span></span>|

## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="e7409-317">Driver ODBC do Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="e7409-317">Microsoft Oracle ODBC Driver</span></span>

<span data-ttu-id="e7409-318">O Driver ODBC do Microsoft SQL Server Oracle suporta as seguintes coleções de esquema específico, além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="e7409-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="e7409-319">Tabelas</span><span class="sxs-lookup"><span data-stu-id="e7409-319">Tables</span></span>

- <span data-ttu-id="e7409-320">Colunas</span><span class="sxs-lookup"><span data-stu-id="e7409-320">Columns</span></span>

- <span data-ttu-id="e7409-321">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="e7409-321">Procedures</span></span>

- <span data-ttu-id="e7409-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="e7409-322">ProcedureColumns</span></span>

- <span data-ttu-id="e7409-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e7409-323">ProcedureParameters</span></span>

- <span data-ttu-id="e7409-324">Exibições</span><span class="sxs-lookup"><span data-stu-id="e7409-324">Views</span></span>

- <span data-ttu-id="e7409-325">Índices</span><span class="sxs-lookup"><span data-stu-id="e7409-325">Indexes</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="e7409-326">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="e7409-326">Tables and Views</span></span>

|<span data-ttu-id="e7409-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e7409-327">ColumnName</span></span>|<span data-ttu-id="e7409-328">DataType</span><span class="sxs-lookup"><span data-stu-id="e7409-328">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e7409-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e7409-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="e7409-330">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-330">String</span></span>|
|<span data-ttu-id="e7409-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e7409-331">TABLE_OWNER</span></span>|<span data-ttu-id="e7409-332">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-332">String</span></span>|
|<span data-ttu-id="e7409-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-333">TABLE_NAME</span></span>|<span data-ttu-id="e7409-334">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-334">String</span></span>|
|<span data-ttu-id="e7409-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e7409-335">TABLE_TYPE</span></span>|<span data-ttu-id="e7409-336">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-336">String</span></span>|
|<span data-ttu-id="e7409-337">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="e7409-337">REMARKS</span></span>|<span data-ttu-id="e7409-338">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-338">String</span></span>|

### <a name="columns"></a><span data-ttu-id="e7409-339">Colunas</span><span class="sxs-lookup"><span data-stu-id="e7409-339">Columns</span></span>

|<span data-ttu-id="e7409-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e7409-340">ColumnName</span></span>|<span data-ttu-id="e7409-341">DataType</span><span class="sxs-lookup"><span data-stu-id="e7409-341">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e7409-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e7409-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="e7409-343">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-343">String</span></span>|
|<span data-ttu-id="e7409-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e7409-344">TABLE_OWNER</span></span>|<span data-ttu-id="e7409-345">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-345">String</span></span>|
|<span data-ttu-id="e7409-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-346">TABLE_NAME</span></span>|<span data-ttu-id="e7409-347">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-347">String</span></span>|
|<span data-ttu-id="e7409-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-348">COLUMN_NAME</span></span>|<span data-ttu-id="e7409-349">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-349">String</span></span>|
|<span data-ttu-id="e7409-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e7409-350">DATA_TYPE</span></span>|<span data-ttu-id="e7409-351">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-351">Int16</span></span>|
|<span data-ttu-id="e7409-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-352">TYPE_NAME</span></span>|<span data-ttu-id="e7409-353">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-353">String</span></span>|
|<span data-ttu-id="e7409-354">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="e7409-354">PRECISION</span></span>|<span data-ttu-id="e7409-355">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-355">Int32</span></span>|
|<span data-ttu-id="e7409-356">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="e7409-356">LENGTH</span></span>|<span data-ttu-id="e7409-357">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-357">Int32</span></span>|
|<span data-ttu-id="e7409-358">ESCALA</span><span class="sxs-lookup"><span data-stu-id="e7409-358">SCALE</span></span>|<span data-ttu-id="e7409-359">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-359">Int16</span></span>|
|<span data-ttu-id="e7409-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="e7409-360">RADIX</span></span>|<span data-ttu-id="e7409-361">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-361">Int16</span></span>|
|<span data-ttu-id="e7409-362">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="e7409-362">NULLABLE</span></span>|<span data-ttu-id="e7409-363">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-363">Int16</span></span>|
|<span data-ttu-id="e7409-364">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="e7409-364">REMARKS</span></span>|<span data-ttu-id="e7409-365">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-365">String</span></span>|
|<span data-ttu-id="e7409-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e7409-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="e7409-367">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-367">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="e7409-368">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="e7409-368">Procedures</span></span>

|<span data-ttu-id="e7409-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e7409-369">ColumnName</span></span>|<span data-ttu-id="e7409-370">DataType</span><span class="sxs-lookup"><span data-stu-id="e7409-370">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e7409-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e7409-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="e7409-372">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-372">String</span></span>|
|<span data-ttu-id="e7409-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e7409-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="e7409-374">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-374">String</span></span>|
|<span data-ttu-id="e7409-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="e7409-376">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-376">String</span></span>|
|<span data-ttu-id="e7409-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="e7409-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="e7409-378">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-378">Int16</span></span>|
|<span data-ttu-id="e7409-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="e7409-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="e7409-380">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-380">Int16</span></span>|
|<span data-ttu-id="e7409-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="e7409-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="e7409-382">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-382">Int16</span></span>|
|<span data-ttu-id="e7409-383">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="e7409-383">REMARKS</span></span>|<span data-ttu-id="e7409-384">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-384">String</span></span>|
|<span data-ttu-id="e7409-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e7409-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="e7409-386">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-386">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="e7409-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="e7409-387">ProcedureColumns</span></span>

|<span data-ttu-id="e7409-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e7409-388">ColumnName</span></span>|<span data-ttu-id="e7409-389">DataType</span><span class="sxs-lookup"><span data-stu-id="e7409-389">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e7409-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e7409-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="e7409-391">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-391">String</span></span>|
|<span data-ttu-id="e7409-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e7409-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="e7409-393">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-393">String</span></span>|
|<span data-ttu-id="e7409-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="e7409-395">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-395">String</span></span>|
|<span data-ttu-id="e7409-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-396">COLUMN_NAME</span></span>|<span data-ttu-id="e7409-397">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-397">String</span></span>|
|<span data-ttu-id="e7409-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="e7409-398">COLUMN_TYPE</span></span>|<span data-ttu-id="e7409-399">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-399">Int16</span></span>|
|<span data-ttu-id="e7409-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e7409-400">DATA_TYPE</span></span>|<span data-ttu-id="e7409-401">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-401">Int16</span></span>|
|<span data-ttu-id="e7409-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-402">TYPE_NAME</span></span>|<span data-ttu-id="e7409-403">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-403">String</span></span>|
|<span data-ttu-id="e7409-404">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="e7409-404">PRECISION</span></span>|<span data-ttu-id="e7409-405">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-405">Int32</span></span>|
|<span data-ttu-id="e7409-406">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="e7409-406">LENGTH</span></span>|<span data-ttu-id="e7409-407">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-407">Int32</span></span>|
|<span data-ttu-id="e7409-408">ESCALA</span><span class="sxs-lookup"><span data-stu-id="e7409-408">SCALE</span></span>|<span data-ttu-id="e7409-409">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-409">Int16</span></span>|
|<span data-ttu-id="e7409-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="e7409-410">RADIX</span></span>|<span data-ttu-id="e7409-411">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-411">Int16</span></span>|
|<span data-ttu-id="e7409-412">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="e7409-412">NULLABLE</span></span>|<span data-ttu-id="e7409-413">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-413">Int16</span></span>|
|<span data-ttu-id="e7409-414">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="e7409-414">REMARKS</span></span>|<span data-ttu-id="e7409-415">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-415">String</span></span>|
|<span data-ttu-id="e7409-416">SOBRECARGA</span><span class="sxs-lookup"><span data-stu-id="e7409-416">OVERLOAD</span></span>|<span data-ttu-id="e7409-417">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-417">Int32</span></span>|
|<span data-ttu-id="e7409-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e7409-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="e7409-419">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-419">Int32</span></span>|

## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="e7409-420">Microsoft Jet ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="e7409-420">Microsoft Jet ODBC Driver</span></span>

<span data-ttu-id="e7409-421">O Driver ODBC do Microsoft Jet suporta as seguintes coleções de esquema específico, além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="e7409-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="e7409-422">Tabelas</span><span class="sxs-lookup"><span data-stu-id="e7409-422">Tables</span></span>

- <span data-ttu-id="e7409-423">Índices</span><span class="sxs-lookup"><span data-stu-id="e7409-423">Indexes</span></span>

- <span data-ttu-id="e7409-424">Colunas</span><span class="sxs-lookup"><span data-stu-id="e7409-424">Columns</span></span>

- <span data-ttu-id="e7409-425">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="e7409-425">Procedures</span></span>

- <span data-ttu-id="e7409-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="e7409-426">ProcedureColumns</span></span>

- <span data-ttu-id="e7409-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e7409-427">ProcedureParameters</span></span>

- <span data-ttu-id="e7409-428">Exibições</span><span class="sxs-lookup"><span data-stu-id="e7409-428">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="e7409-429">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="e7409-429">Tables and Views</span></span>

|<span data-ttu-id="e7409-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e7409-430">ColumnName</span></span>|<span data-ttu-id="e7409-431">DataType</span><span class="sxs-lookup"><span data-stu-id="e7409-431">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e7409-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e7409-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="e7409-433">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-433">String</span></span>|
|<span data-ttu-id="e7409-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e7409-434">TABLE_OWNER</span></span>|<span data-ttu-id="e7409-435">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-435">String</span></span>|
|<span data-ttu-id="e7409-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-436">TABLE_NAME</span></span>|<span data-ttu-id="e7409-437">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-437">String</span></span>|
|<span data-ttu-id="e7409-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e7409-438">TABLE_TYPE</span></span>|<span data-ttu-id="e7409-439">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-439">String</span></span>|
|<span data-ttu-id="e7409-440">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="e7409-440">REMARKS</span></span>|<span data-ttu-id="e7409-441">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-441">String</span></span>|

### <a name="columns"></a><span data-ttu-id="e7409-442">Colunas</span><span class="sxs-lookup"><span data-stu-id="e7409-442">Columns</span></span>

|<span data-ttu-id="e7409-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e7409-443">ColumnName</span></span>|<span data-ttu-id="e7409-444">DataType</span><span class="sxs-lookup"><span data-stu-id="e7409-444">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e7409-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e7409-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="e7409-446">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-446">String</span></span>|
|<span data-ttu-id="e7409-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e7409-447">TABLE_OWNER</span></span>|<span data-ttu-id="e7409-448">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-448">String</span></span>|
|<span data-ttu-id="e7409-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-449">TABLE_NAME</span></span>|<span data-ttu-id="e7409-450">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-450">String</span></span>|
|<span data-ttu-id="e7409-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-451">COLUMN_NAME</span></span>|<span data-ttu-id="e7409-452">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-452">String</span></span>|
|<span data-ttu-id="e7409-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e7409-453">DATA_TYPE</span></span>|<span data-ttu-id="e7409-454">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-454">Int16</span></span>|
|<span data-ttu-id="e7409-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-455">TYPE_NAME</span></span>|<span data-ttu-id="e7409-456">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-456">String</span></span>|
|<span data-ttu-id="e7409-457">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="e7409-457">PRECISION</span></span>|<span data-ttu-id="e7409-458">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-458">Int32</span></span>|
|<span data-ttu-id="e7409-459">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="e7409-459">LENGTH</span></span>|<span data-ttu-id="e7409-460">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-460">Int32</span></span>|
|<span data-ttu-id="e7409-461">ESCALA</span><span class="sxs-lookup"><span data-stu-id="e7409-461">SCALE</span></span>|<span data-ttu-id="e7409-462">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-462">Int16</span></span>|
|<span data-ttu-id="e7409-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="e7409-463">RADIX</span></span>|<span data-ttu-id="e7409-464">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-464">Int16</span></span>|
|<span data-ttu-id="e7409-465">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="e7409-465">NULLABLE</span></span>|<span data-ttu-id="e7409-466">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-466">Int16</span></span>|
|<span data-ttu-id="e7409-467">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="e7409-467">REMARKS</span></span>|<span data-ttu-id="e7409-468">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-468">String</span></span>|
|<span data-ttu-id="e7409-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e7409-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="e7409-470">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-470">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="e7409-471">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="e7409-471">Procedures</span></span>

|<span data-ttu-id="e7409-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e7409-472">ColumnName</span></span>|<span data-ttu-id="e7409-473">DataType</span><span class="sxs-lookup"><span data-stu-id="e7409-473">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e7409-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e7409-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="e7409-475">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-475">String</span></span>|
|<span data-ttu-id="e7409-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e7409-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="e7409-477">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-477">String</span></span>|
|<span data-ttu-id="e7409-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="e7409-479">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-479">String</span></span>|
|<span data-ttu-id="e7409-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="e7409-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="e7409-481">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-481">Int16</span></span>|
|<span data-ttu-id="e7409-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="e7409-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="e7409-483">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-483">Int16</span></span>|
|<span data-ttu-id="e7409-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="e7409-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="e7409-485">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-485">Int16</span></span>|
|<span data-ttu-id="e7409-486">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="e7409-486">REMARKS</span></span>|<span data-ttu-id="e7409-487">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-487">String</span></span>|
|<span data-ttu-id="e7409-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e7409-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="e7409-489">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-489">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="e7409-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="e7409-490">ProcedureColumns</span></span>

|<span data-ttu-id="e7409-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e7409-491">ColumnName</span></span>|<span data-ttu-id="e7409-492">DataType</span><span class="sxs-lookup"><span data-stu-id="e7409-492">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e7409-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e7409-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="e7409-494">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-494">String</span></span>|
|<span data-ttu-id="e7409-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e7409-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="e7409-496">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-496">String</span></span>|
|<span data-ttu-id="e7409-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="e7409-498">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-498">String</span></span>|
|<span data-ttu-id="e7409-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-499">COLUMN_NAME</span></span>|<span data-ttu-id="e7409-500">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-500">String</span></span>|
|<span data-ttu-id="e7409-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="e7409-501">COLUMN_TYPE</span></span>|<span data-ttu-id="e7409-502">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-502">Int16</span></span>|
|<span data-ttu-id="e7409-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e7409-503">DATA_TYPE</span></span>|<span data-ttu-id="e7409-504">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-504">Int16</span></span>|
|<span data-ttu-id="e7409-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-505">TYPE_NAME</span></span>|<span data-ttu-id="e7409-506">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-506">String</span></span>|
|<span data-ttu-id="e7409-507">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="e7409-507">PRECISION</span></span>|<span data-ttu-id="e7409-508">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-508">Int32</span></span>|
|<span data-ttu-id="e7409-509">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="e7409-509">LENGTH</span></span>|<span data-ttu-id="e7409-510">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-510">Int32</span></span>|
|<span data-ttu-id="e7409-511">ESCALA</span><span class="sxs-lookup"><span data-stu-id="e7409-511">SCALE</span></span>|<span data-ttu-id="e7409-512">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-512">Int16</span></span>|
|<span data-ttu-id="e7409-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="e7409-513">RADIX</span></span>|<span data-ttu-id="e7409-514">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-514">Int16</span></span>|
|<span data-ttu-id="e7409-515">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="e7409-515">NULLABLE</span></span>|<span data-ttu-id="e7409-516">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-516">Int16</span></span>|
|<span data-ttu-id="e7409-517">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="e7409-517">REMARKS</span></span>|<span data-ttu-id="e7409-518">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-518">String</span></span>|
|<span data-ttu-id="e7409-519">SOBRECARGA</span><span class="sxs-lookup"><span data-stu-id="e7409-519">OVERLOAD</span></span>|<span data-ttu-id="e7409-520">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-520">Int32</span></span>|
|<span data-ttu-id="e7409-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e7409-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="e7409-522">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-522">Int32</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="e7409-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e7409-523">ProcedureParameters</span></span>

|<span data-ttu-id="e7409-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e7409-524">ColumnName</span></span>|<span data-ttu-id="e7409-525">DataType</span><span class="sxs-lookup"><span data-stu-id="e7409-525">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e7409-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="e7409-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="e7409-527">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-527">String</span></span>|
|<span data-ttu-id="e7409-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="e7409-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="e7409-529">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-529">String</span></span>|
|<span data-ttu-id="e7409-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="e7409-531">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-531">String</span></span>|
|<span data-ttu-id="e7409-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-532">COLUMN_NAME</span></span>|<span data-ttu-id="e7409-533">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-533">String</span></span>|
|<span data-ttu-id="e7409-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="e7409-534">COLUMN_TYPE</span></span>|<span data-ttu-id="e7409-535">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-535">Int16</span></span>|
|<span data-ttu-id="e7409-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e7409-536">DATA_TYPE</span></span>|<span data-ttu-id="e7409-537">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-537">Int16</span></span>|
|<span data-ttu-id="e7409-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e7409-538">TYPE_NAME</span></span>|<span data-ttu-id="e7409-539">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-539">String</span></span>|
|<span data-ttu-id="e7409-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="e7409-540">COLUMN_SIZE</span></span>|<span data-ttu-id="e7409-541">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-541">Int32</span></span>|
|<span data-ttu-id="e7409-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e7409-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="e7409-543">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-543">Int32</span></span>|
|<span data-ttu-id="e7409-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="e7409-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="e7409-545">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-545">Int16</span></span>|
|<span data-ttu-id="e7409-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="e7409-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="e7409-547">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-547">Int16</span></span>|
|<span data-ttu-id="e7409-548">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="e7409-548">NULLABLE</span></span>|<span data-ttu-id="e7409-549">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-549">Int16</span></span>|
|<span data-ttu-id="e7409-550">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="e7409-550">REMARKS</span></span>|<span data-ttu-id="e7409-551">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-551">String</span></span>|
|<span data-ttu-id="e7409-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="e7409-552">COLUMN_DEF</span></span>|<span data-ttu-id="e7409-553">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-553">String</span></span>|
|<span data-ttu-id="e7409-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e7409-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="e7409-555">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-555">Int16</span></span>|
|<span data-ttu-id="e7409-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="e7409-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="e7409-557">Int16</span><span class="sxs-lookup"><span data-stu-id="e7409-557">Int16</span></span>|
|<span data-ttu-id="e7409-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e7409-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="e7409-559">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-559">Int32</span></span>|
|<span data-ttu-id="e7409-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e7409-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="e7409-561">Int32</span><span class="sxs-lookup"><span data-stu-id="e7409-561">Int32</span></span>|
|<span data-ttu-id="e7409-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e7409-562">IS_NULLABLE</span></span>|<span data-ttu-id="e7409-563">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e7409-563">String</span></span>|

## <a name="see-also"></a><span data-ttu-id="e7409-564">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7409-564">See also</span></span>

- <span data-ttu-id="e7409-565">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="e7409-565">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
