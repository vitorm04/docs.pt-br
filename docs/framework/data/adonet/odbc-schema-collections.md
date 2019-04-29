---
title: Coleções de esquema ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: ffe80120ceffbe29c0a117cf1194860c5782be8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772041"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="18129-102">Coleções de esquema ODBC</span><span class="sxs-lookup"><span data-stu-id="18129-102">ODBC Schema Collections</span></span>

<span data-ttu-id="18129-103">Esta seção discute o suporte de coleção de esquema para os drivers ODBC para Microsoft SQL Server, Oracle e Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="18129-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>

## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="18129-104">Driver ODBC do Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="18129-104">Microsoft SQL Server ODBC Driver</span></span>

<span data-ttu-id="18129-105">O Driver ODBC do Microsoft SQL Server suporta as seguintes coleções de esquema específico, além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="18129-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="18129-106">Tabelas</span><span class="sxs-lookup"><span data-stu-id="18129-106">Tables</span></span>

- <span data-ttu-id="18129-107">Índices</span><span class="sxs-lookup"><span data-stu-id="18129-107">Indexes</span></span>

- <span data-ttu-id="18129-108">Colunas</span><span class="sxs-lookup"><span data-stu-id="18129-108">Columns</span></span>

- <span data-ttu-id="18129-109">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="18129-109">Procedures</span></span>

- <span data-ttu-id="18129-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="18129-110">ProcedureColumns</span></span>

- <span data-ttu-id="18129-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="18129-111">ProcedureParameters</span></span>

- <span data-ttu-id="18129-112">Exibições</span><span class="sxs-lookup"><span data-stu-id="18129-112">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="18129-113">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="18129-113">Tables and Views</span></span>

|<span data-ttu-id="18129-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="18129-114">ColumnName</span></span>|<span data-ttu-id="18129-115">DataType</span><span class="sxs-lookup"><span data-stu-id="18129-115">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="18129-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="18129-116">TABLE_CAT</span></span>|<span data-ttu-id="18129-117">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-117">String</span></span>|
|<span data-ttu-id="18129-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="18129-118">TABLE_SCHEM</span></span>|<span data-ttu-id="18129-119">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-119">String</span></span>|
|<span data-ttu-id="18129-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-120">TABLE_NAME</span></span>|<span data-ttu-id="18129-121">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-121">String</span></span>|
|<span data-ttu-id="18129-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="18129-122">TABLE_TYPE</span></span>|<span data-ttu-id="18129-123">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-123">String</span></span>|
|<span data-ttu-id="18129-124">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="18129-124">REMARKS</span></span>|<span data-ttu-id="18129-125">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-125">String</span></span>|

### <a name="indexes"></a><span data-ttu-id="18129-126">Índices</span><span class="sxs-lookup"><span data-stu-id="18129-126">Indexes</span></span>

|<span data-ttu-id="18129-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="18129-127">ColumnName</span></span>|<span data-ttu-id="18129-128">DataType</span><span class="sxs-lookup"><span data-stu-id="18129-128">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="18129-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="18129-129">TABLE_CAT</span></span>|<span data-ttu-id="18129-130">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-130">String</span></span>|
|<span data-ttu-id="18129-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="18129-131">TABLE_SCHEM</span></span>|<span data-ttu-id="18129-132">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-132">String</span></span>|
|<span data-ttu-id="18129-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-133">TABLE_NAME</span></span>|<span data-ttu-id="18129-134">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-134">String</span></span>|
|<span data-ttu-id="18129-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="18129-135">NON_UNIQUE</span></span>|<span data-ttu-id="18129-136">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-136">Int16</span></span>|
|<span data-ttu-id="18129-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="18129-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="18129-138">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-138">String</span></span>|
|<span data-ttu-id="18129-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-139">INDEX_NAME</span></span>|<span data-ttu-id="18129-140">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-140">String</span></span>|
|<span data-ttu-id="18129-141">TIPO</span><span class="sxs-lookup"><span data-stu-id="18129-141">TYPE</span></span>|<span data-ttu-id="18129-142">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-142">Int16</span></span>|
|<span data-ttu-id="18129-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="18129-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="18129-144">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-144">Int16</span></span>|
|<span data-ttu-id="18129-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-145">COLUMN_NAME</span></span>|<span data-ttu-id="18129-146">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-146">String</span></span>|
|<span data-ttu-id="18129-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="18129-147">ASC_OR_DESC</span></span>|<span data-ttu-id="18129-148">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-148">String</span></span>|
|<span data-ttu-id="18129-149">CARDINALIDADE</span><span class="sxs-lookup"><span data-stu-id="18129-149">CARDINALITY</span></span>|<span data-ttu-id="18129-150">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-150">Int32</span></span>|
|<span data-ttu-id="18129-151">PÁGINAS</span><span class="sxs-lookup"><span data-stu-id="18129-151">PAGES</span></span>|<span data-ttu-id="18129-152">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-152">Int32</span></span>|
|<span data-ttu-id="18129-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="18129-153">FILTER_CONDITION</span></span>|<span data-ttu-id="18129-154">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-154">String</span></span>|
|<span data-ttu-id="18129-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="18129-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="18129-156">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-156">String</span></span>|
|<span data-ttu-id="18129-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="18129-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="18129-158">Byte</span><span class="sxs-lookup"><span data-stu-id="18129-158">Byte</span></span>|

### <a name="columns"></a><span data-ttu-id="18129-159">Colunas</span><span class="sxs-lookup"><span data-stu-id="18129-159">Columns</span></span>

|<span data-ttu-id="18129-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="18129-160">ColumnName</span></span>|<span data-ttu-id="18129-161">DataType</span><span class="sxs-lookup"><span data-stu-id="18129-161">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="18129-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="18129-162">TABLE_CAT</span></span>|<span data-ttu-id="18129-163">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-163">String</span></span>|
|<span data-ttu-id="18129-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="18129-164">TABLE_SCHEM</span></span>|<span data-ttu-id="18129-165">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-165">String</span></span>|
|<span data-ttu-id="18129-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-166">TABLE_NAME</span></span>|<span data-ttu-id="18129-167">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-167">String</span></span>|
|<span data-ttu-id="18129-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-168">COLUMN_NAME</span></span>|<span data-ttu-id="18129-169">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-169">String</span></span>|
|<span data-ttu-id="18129-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="18129-170">DATA_TYPE</span></span>|<span data-ttu-id="18129-171">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-171">Int16</span></span>|
|<span data-ttu-id="18129-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-172">TYPE_NAME</span></span>|<span data-ttu-id="18129-173">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-173">String</span></span>|
|<span data-ttu-id="18129-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="18129-174">COLUMN_SIZE</span></span>|<span data-ttu-id="18129-175">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-175">Int32</span></span>|
|<span data-ttu-id="18129-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="18129-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="18129-177">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-177">Int32</span></span>|
|<span data-ttu-id="18129-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="18129-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="18129-179">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-179">Int16</span></span>|
|<span data-ttu-id="18129-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="18129-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="18129-181">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-181">Int16</span></span>|
|<span data-ttu-id="18129-182">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="18129-182">NULLABLE</span></span>|<span data-ttu-id="18129-183">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-183">Int16</span></span>|
|<span data-ttu-id="18129-184">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="18129-184">REMARKS</span></span>|<span data-ttu-id="18129-185">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-185">String</span></span>|
|<span data-ttu-id="18129-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="18129-186">COLUMN_DEF</span></span>|<span data-ttu-id="18129-187">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-187">String</span></span>|
|<span data-ttu-id="18129-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="18129-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="18129-189">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-189">Int16</span></span>|
|<span data-ttu-id="18129-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="18129-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="18129-191">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-191">Int16</span></span>|
|<span data-ttu-id="18129-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="18129-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="18129-193">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-193">Int32</span></span>|
|<span data-ttu-id="18129-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="18129-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="18129-195">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-195">Int32</span></span>|
|<span data-ttu-id="18129-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="18129-196">IS_NULLABLE</span></span>|<span data-ttu-id="18129-197">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-197">String</span></span>|
|<span data-ttu-id="18129-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="18129-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="18129-199">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-199">String</span></span>|
|<span data-ttu-id="18129-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="18129-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="18129-201">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-201">String</span></span>|
|<span data-ttu-id="18129-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="18129-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="18129-203">Byte</span><span class="sxs-lookup"><span data-stu-id="18129-203">Byte</span></span>|

### <a name="procedures"></a><span data-ttu-id="18129-204">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="18129-204">Procedures</span></span>

|<span data-ttu-id="18129-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="18129-205">ColumnName</span></span>|<span data-ttu-id="18129-206">DataType</span><span class="sxs-lookup"><span data-stu-id="18129-206">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="18129-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="18129-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="18129-208">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-208">String</span></span>|
|<span data-ttu-id="18129-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="18129-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="18129-210">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-210">String</span></span>|
|<span data-ttu-id="18129-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="18129-212">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-212">String</span></span>|
|<span data-ttu-id="18129-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="18129-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="18129-214">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-214">Int32</span></span>|
|<span data-ttu-id="18129-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="18129-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="18129-216">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-216">Int32</span></span>|
|<span data-ttu-id="18129-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="18129-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="18129-218">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-218">Int32</span></span>|
|<span data-ttu-id="18129-219">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="18129-219">REMARKS</span></span>|<span data-ttu-id="18129-220">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-220">String</span></span>|
|<span data-ttu-id="18129-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="18129-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="18129-222">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-222">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="18129-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="18129-223">ProcedureColumns</span></span>

|<span data-ttu-id="18129-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="18129-224">ColumnName</span></span>|<span data-ttu-id="18129-225">DataType</span><span class="sxs-lookup"><span data-stu-id="18129-225">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="18129-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="18129-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="18129-227">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-227">String</span></span>|
|<span data-ttu-id="18129-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="18129-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="18129-229">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-229">String</span></span>|
|<span data-ttu-id="18129-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="18129-231">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-231">String</span></span>|
|<span data-ttu-id="18129-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-232">COLUMN_NAME</span></span>|<span data-ttu-id="18129-233">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-233">String</span></span>|
|<span data-ttu-id="18129-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="18129-234">COLUMN_TYPE</span></span>|<span data-ttu-id="18129-235">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-235">Int16</span></span>|
|<span data-ttu-id="18129-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="18129-236">DATA_TYPE</span></span>|<span data-ttu-id="18129-237">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-237">Int16</span></span>|
|<span data-ttu-id="18129-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-238">TYPE_NAME</span></span>|<span data-ttu-id="18129-239">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-239">String</span></span>|
|<span data-ttu-id="18129-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="18129-240">COLUMN_SIZE</span></span>|<span data-ttu-id="18129-241">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-241">Int32</span></span>|
|<span data-ttu-id="18129-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="18129-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="18129-243">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-243">Int32</span></span>|
|<span data-ttu-id="18129-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="18129-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="18129-245">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-245">Int16</span></span>|
|<span data-ttu-id="18129-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="18129-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="18129-247">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-247">Int16</span></span>|
|<span data-ttu-id="18129-248">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="18129-248">NULLABLE</span></span>|<span data-ttu-id="18129-249">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-249">Int16</span></span>|
|<span data-ttu-id="18129-250">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="18129-250">REMARKS</span></span>|<span data-ttu-id="18129-251">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-251">String</span></span>|
|<span data-ttu-id="18129-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="18129-252">COLUMN_DEF</span></span>|<span data-ttu-id="18129-253">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-253">String</span></span>|
|<span data-ttu-id="18129-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="18129-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="18129-255">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-255">Int16</span></span>|
|<span data-ttu-id="18129-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="18129-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="18129-257">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-257">Int16</span></span>|
|<span data-ttu-id="18129-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="18129-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="18129-259">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-259">Int32</span></span>|
|<span data-ttu-id="18129-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="18129-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="18129-261">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-261">Int32</span></span>|
|<span data-ttu-id="18129-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="18129-262">IS_NULLABLE</span></span>|<span data-ttu-id="18129-263">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-263">String</span></span>|
|<span data-ttu-id="18129-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="18129-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="18129-265">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-265">String</span></span>|
|<span data-ttu-id="18129-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="18129-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="18129-267">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-267">String</span></span>|
|<span data-ttu-id="18129-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="18129-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="18129-269">Byte</span><span class="sxs-lookup"><span data-stu-id="18129-269">Byte</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="18129-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="18129-270">ProcedureParameters</span></span>

|<span data-ttu-id="18129-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="18129-271">ColumnName</span></span>|<span data-ttu-id="18129-272">DataType</span><span class="sxs-lookup"><span data-stu-id="18129-272">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="18129-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="18129-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="18129-274">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-274">String</span></span>|
|<span data-ttu-id="18129-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="18129-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="18129-276">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-276">String</span></span>|
|<span data-ttu-id="18129-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="18129-278">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-278">String</span></span>|
|<span data-ttu-id="18129-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-279">COLUMN_NAME</span></span>|<span data-ttu-id="18129-280">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-280">String</span></span>|
|<span data-ttu-id="18129-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="18129-281">COLUMN_TYPE</span></span>|<span data-ttu-id="18129-282">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-282">Int16</span></span>|
|<span data-ttu-id="18129-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="18129-283">DATA_TYPE</span></span>|<span data-ttu-id="18129-284">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-284">Int16</span></span>|
|<span data-ttu-id="18129-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-285">TYPE_NAME</span></span>|<span data-ttu-id="18129-286">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-286">String</span></span>|
|<span data-ttu-id="18129-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="18129-287">COLUMN_SIZE</span></span>|<span data-ttu-id="18129-288">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-288">Int32</span></span>|
|<span data-ttu-id="18129-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="18129-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="18129-290">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-290">Int32</span></span>|
|<span data-ttu-id="18129-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="18129-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="18129-292">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-292">Int16</span></span>|
|<span data-ttu-id="18129-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="18129-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="18129-294">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-294">Int16</span></span>|
|<span data-ttu-id="18129-295">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="18129-295">NULLABLE</span></span>|<span data-ttu-id="18129-296">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-296">Int16</span></span>|
|<span data-ttu-id="18129-297">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="18129-297">REMARKS</span></span>|<span data-ttu-id="18129-298">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-298">String</span></span>|
|<span data-ttu-id="18129-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="18129-299">COLUMN_DEF</span></span>|<span data-ttu-id="18129-300">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-300">String</span></span>|
|<span data-ttu-id="18129-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="18129-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="18129-302">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-302">Int16</span></span>|
|<span data-ttu-id="18129-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="18129-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="18129-304">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-304">Int16</span></span>|
|<span data-ttu-id="18129-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="18129-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="18129-306">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-306">Int32</span></span>|
|<span data-ttu-id="18129-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="18129-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="18129-308">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-308">Int32</span></span>|
|<span data-ttu-id="18129-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="18129-309">IS_NULLABLE</span></span>|<span data-ttu-id="18129-310">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-310">String</span></span>|
|<span data-ttu-id="18129-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="18129-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="18129-312">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-312">String</span></span>|
|<span data-ttu-id="18129-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="18129-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="18129-314">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-314">String</span></span>|
|<span data-ttu-id="18129-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="18129-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="18129-316">Byte</span><span class="sxs-lookup"><span data-stu-id="18129-316">Byte</span></span>|

## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="18129-317">Driver ODBC do Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="18129-317">Microsoft Oracle ODBC Driver</span></span>

<span data-ttu-id="18129-318">O Driver ODBC do Microsoft SQL Server Oracle suporta as seguintes coleções de esquema específico, além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="18129-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="18129-319">Tabelas</span><span class="sxs-lookup"><span data-stu-id="18129-319">Tables</span></span>

- <span data-ttu-id="18129-320">Colunas</span><span class="sxs-lookup"><span data-stu-id="18129-320">Columns</span></span>

- <span data-ttu-id="18129-321">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="18129-321">Procedures</span></span>

- <span data-ttu-id="18129-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="18129-322">ProcedureColumns</span></span>

- <span data-ttu-id="18129-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="18129-323">ProcedureParameters</span></span>

- <span data-ttu-id="18129-324">Exibições</span><span class="sxs-lookup"><span data-stu-id="18129-324">Views</span></span>

- <span data-ttu-id="18129-325">Índices</span><span class="sxs-lookup"><span data-stu-id="18129-325">Indexes</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="18129-326">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="18129-326">Tables and Views</span></span>

|<span data-ttu-id="18129-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="18129-327">ColumnName</span></span>|<span data-ttu-id="18129-328">DataType</span><span class="sxs-lookup"><span data-stu-id="18129-328">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="18129-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="18129-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="18129-330">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-330">String</span></span>|
|<span data-ttu-id="18129-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="18129-331">TABLE_OWNER</span></span>|<span data-ttu-id="18129-332">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-332">String</span></span>|
|<span data-ttu-id="18129-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-333">TABLE_NAME</span></span>|<span data-ttu-id="18129-334">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-334">String</span></span>|
|<span data-ttu-id="18129-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="18129-335">TABLE_TYPE</span></span>|<span data-ttu-id="18129-336">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-336">String</span></span>|
|<span data-ttu-id="18129-337">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="18129-337">REMARKS</span></span>|<span data-ttu-id="18129-338">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-338">String</span></span>|

### <a name="columns"></a><span data-ttu-id="18129-339">Colunas</span><span class="sxs-lookup"><span data-stu-id="18129-339">Columns</span></span>

|<span data-ttu-id="18129-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="18129-340">ColumnName</span></span>|<span data-ttu-id="18129-341">DataType</span><span class="sxs-lookup"><span data-stu-id="18129-341">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="18129-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="18129-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="18129-343">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-343">String</span></span>|
|<span data-ttu-id="18129-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="18129-344">TABLE_OWNER</span></span>|<span data-ttu-id="18129-345">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-345">String</span></span>|
|<span data-ttu-id="18129-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-346">TABLE_NAME</span></span>|<span data-ttu-id="18129-347">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-347">String</span></span>|
|<span data-ttu-id="18129-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-348">COLUMN_NAME</span></span>|<span data-ttu-id="18129-349">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-349">String</span></span>|
|<span data-ttu-id="18129-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="18129-350">DATA_TYPE</span></span>|<span data-ttu-id="18129-351">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-351">Int16</span></span>|
|<span data-ttu-id="18129-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-352">TYPE_NAME</span></span>|<span data-ttu-id="18129-353">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-353">String</span></span>|
|<span data-ttu-id="18129-354">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="18129-354">PRECISION</span></span>|<span data-ttu-id="18129-355">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-355">Int32</span></span>|
|<span data-ttu-id="18129-356">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="18129-356">LENGTH</span></span>|<span data-ttu-id="18129-357">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-357">Int32</span></span>|
|<span data-ttu-id="18129-358">ESCALA</span><span class="sxs-lookup"><span data-stu-id="18129-358">SCALE</span></span>|<span data-ttu-id="18129-359">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-359">Int16</span></span>|
|<span data-ttu-id="18129-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="18129-360">RADIX</span></span>|<span data-ttu-id="18129-361">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-361">Int16</span></span>|
|<span data-ttu-id="18129-362">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="18129-362">NULLABLE</span></span>|<span data-ttu-id="18129-363">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-363">Int16</span></span>|
|<span data-ttu-id="18129-364">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="18129-364">REMARKS</span></span>|<span data-ttu-id="18129-365">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-365">String</span></span>|
|<span data-ttu-id="18129-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="18129-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="18129-367">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-367">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="18129-368">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="18129-368">Procedures</span></span>

|<span data-ttu-id="18129-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="18129-369">ColumnName</span></span>|<span data-ttu-id="18129-370">DataType</span><span class="sxs-lookup"><span data-stu-id="18129-370">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="18129-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="18129-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="18129-372">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-372">String</span></span>|
|<span data-ttu-id="18129-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="18129-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="18129-374">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-374">String</span></span>|
|<span data-ttu-id="18129-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="18129-376">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-376">String</span></span>|
|<span data-ttu-id="18129-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="18129-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="18129-378">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-378">Int16</span></span>|
|<span data-ttu-id="18129-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="18129-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="18129-380">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-380">Int16</span></span>|
|<span data-ttu-id="18129-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="18129-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="18129-382">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-382">Int16</span></span>|
|<span data-ttu-id="18129-383">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="18129-383">REMARKS</span></span>|<span data-ttu-id="18129-384">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-384">String</span></span>|
|<span data-ttu-id="18129-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="18129-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="18129-386">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-386">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="18129-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="18129-387">ProcedureColumns</span></span>

|<span data-ttu-id="18129-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="18129-388">ColumnName</span></span>|<span data-ttu-id="18129-389">DataType</span><span class="sxs-lookup"><span data-stu-id="18129-389">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="18129-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="18129-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="18129-391">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-391">String</span></span>|
|<span data-ttu-id="18129-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="18129-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="18129-393">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-393">String</span></span>|
|<span data-ttu-id="18129-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="18129-395">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-395">String</span></span>|
|<span data-ttu-id="18129-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-396">COLUMN_NAME</span></span>|<span data-ttu-id="18129-397">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-397">String</span></span>|
|<span data-ttu-id="18129-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="18129-398">COLUMN_TYPE</span></span>|<span data-ttu-id="18129-399">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-399">Int16</span></span>|
|<span data-ttu-id="18129-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="18129-400">DATA_TYPE</span></span>|<span data-ttu-id="18129-401">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-401">Int16</span></span>|
|<span data-ttu-id="18129-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-402">TYPE_NAME</span></span>|<span data-ttu-id="18129-403">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-403">String</span></span>|
|<span data-ttu-id="18129-404">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="18129-404">PRECISION</span></span>|<span data-ttu-id="18129-405">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-405">Int32</span></span>|
|<span data-ttu-id="18129-406">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="18129-406">LENGTH</span></span>|<span data-ttu-id="18129-407">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-407">Int32</span></span>|
|<span data-ttu-id="18129-408">ESCALA</span><span class="sxs-lookup"><span data-stu-id="18129-408">SCALE</span></span>|<span data-ttu-id="18129-409">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-409">Int16</span></span>|
|<span data-ttu-id="18129-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="18129-410">RADIX</span></span>|<span data-ttu-id="18129-411">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-411">Int16</span></span>|
|<span data-ttu-id="18129-412">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="18129-412">NULLABLE</span></span>|<span data-ttu-id="18129-413">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-413">Int16</span></span>|
|<span data-ttu-id="18129-414">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="18129-414">REMARKS</span></span>|<span data-ttu-id="18129-415">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-415">String</span></span>|
|<span data-ttu-id="18129-416">SOBRECARGA</span><span class="sxs-lookup"><span data-stu-id="18129-416">OVERLOAD</span></span>|<span data-ttu-id="18129-417">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-417">Int32</span></span>|
|<span data-ttu-id="18129-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="18129-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="18129-419">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-419">Int32</span></span>|

## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="18129-420">Microsoft Jet ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="18129-420">Microsoft Jet ODBC Driver</span></span>

<span data-ttu-id="18129-421">O Driver ODBC do Microsoft Jet suporta as seguintes coleções de esquema específico, além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="18129-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="18129-422">Tabelas</span><span class="sxs-lookup"><span data-stu-id="18129-422">Tables</span></span>

- <span data-ttu-id="18129-423">Índices</span><span class="sxs-lookup"><span data-stu-id="18129-423">Indexes</span></span>

- <span data-ttu-id="18129-424">Colunas</span><span class="sxs-lookup"><span data-stu-id="18129-424">Columns</span></span>

- <span data-ttu-id="18129-425">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="18129-425">Procedures</span></span>

- <span data-ttu-id="18129-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="18129-426">ProcedureColumns</span></span>

- <span data-ttu-id="18129-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="18129-427">ProcedureParameters</span></span>

- <span data-ttu-id="18129-428">Exibições</span><span class="sxs-lookup"><span data-stu-id="18129-428">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="18129-429">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="18129-429">Tables and Views</span></span>

|<span data-ttu-id="18129-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="18129-430">ColumnName</span></span>|<span data-ttu-id="18129-431">DataType</span><span class="sxs-lookup"><span data-stu-id="18129-431">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="18129-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="18129-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="18129-433">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-433">String</span></span>|
|<span data-ttu-id="18129-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="18129-434">TABLE_OWNER</span></span>|<span data-ttu-id="18129-435">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-435">String</span></span>|
|<span data-ttu-id="18129-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-436">TABLE_NAME</span></span>|<span data-ttu-id="18129-437">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-437">String</span></span>|
|<span data-ttu-id="18129-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="18129-438">TABLE_TYPE</span></span>|<span data-ttu-id="18129-439">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-439">String</span></span>|
|<span data-ttu-id="18129-440">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="18129-440">REMARKS</span></span>|<span data-ttu-id="18129-441">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-441">String</span></span>|

### <a name="columns"></a><span data-ttu-id="18129-442">Colunas</span><span class="sxs-lookup"><span data-stu-id="18129-442">Columns</span></span>

|<span data-ttu-id="18129-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="18129-443">ColumnName</span></span>|<span data-ttu-id="18129-444">DataType</span><span class="sxs-lookup"><span data-stu-id="18129-444">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="18129-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="18129-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="18129-446">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-446">String</span></span>|
|<span data-ttu-id="18129-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="18129-447">TABLE_OWNER</span></span>|<span data-ttu-id="18129-448">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-448">String</span></span>|
|<span data-ttu-id="18129-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-449">TABLE_NAME</span></span>|<span data-ttu-id="18129-450">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-450">String</span></span>|
|<span data-ttu-id="18129-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-451">COLUMN_NAME</span></span>|<span data-ttu-id="18129-452">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-452">String</span></span>|
|<span data-ttu-id="18129-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="18129-453">DATA_TYPE</span></span>|<span data-ttu-id="18129-454">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-454">Int16</span></span>|
|<span data-ttu-id="18129-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-455">TYPE_NAME</span></span>|<span data-ttu-id="18129-456">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-456">String</span></span>|
|<span data-ttu-id="18129-457">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="18129-457">PRECISION</span></span>|<span data-ttu-id="18129-458">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-458">Int32</span></span>|
|<span data-ttu-id="18129-459">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="18129-459">LENGTH</span></span>|<span data-ttu-id="18129-460">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-460">Int32</span></span>|
|<span data-ttu-id="18129-461">ESCALA</span><span class="sxs-lookup"><span data-stu-id="18129-461">SCALE</span></span>|<span data-ttu-id="18129-462">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-462">Int16</span></span>|
|<span data-ttu-id="18129-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="18129-463">RADIX</span></span>|<span data-ttu-id="18129-464">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-464">Int16</span></span>|
|<span data-ttu-id="18129-465">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="18129-465">NULLABLE</span></span>|<span data-ttu-id="18129-466">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-466">Int16</span></span>|
|<span data-ttu-id="18129-467">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="18129-467">REMARKS</span></span>|<span data-ttu-id="18129-468">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-468">String</span></span>|
|<span data-ttu-id="18129-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="18129-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="18129-470">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-470">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="18129-471">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="18129-471">Procedures</span></span>

|<span data-ttu-id="18129-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="18129-472">ColumnName</span></span>|<span data-ttu-id="18129-473">DataType</span><span class="sxs-lookup"><span data-stu-id="18129-473">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="18129-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="18129-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="18129-475">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-475">String</span></span>|
|<span data-ttu-id="18129-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="18129-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="18129-477">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-477">String</span></span>|
|<span data-ttu-id="18129-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="18129-479">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-479">String</span></span>|
|<span data-ttu-id="18129-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="18129-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="18129-481">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-481">Int16</span></span>|
|<span data-ttu-id="18129-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="18129-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="18129-483">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-483">Int16</span></span>|
|<span data-ttu-id="18129-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="18129-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="18129-485">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-485">Int16</span></span>|
|<span data-ttu-id="18129-486">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="18129-486">REMARKS</span></span>|<span data-ttu-id="18129-487">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-487">String</span></span>|
|<span data-ttu-id="18129-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="18129-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="18129-489">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-489">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="18129-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="18129-490">ProcedureColumns</span></span>

|<span data-ttu-id="18129-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="18129-491">ColumnName</span></span>|<span data-ttu-id="18129-492">DataType</span><span class="sxs-lookup"><span data-stu-id="18129-492">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="18129-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="18129-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="18129-494">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-494">String</span></span>|
|<span data-ttu-id="18129-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="18129-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="18129-496">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-496">String</span></span>|
|<span data-ttu-id="18129-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="18129-498">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-498">String</span></span>|
|<span data-ttu-id="18129-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-499">COLUMN_NAME</span></span>|<span data-ttu-id="18129-500">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-500">String</span></span>|
|<span data-ttu-id="18129-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="18129-501">COLUMN_TYPE</span></span>|<span data-ttu-id="18129-502">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-502">Int16</span></span>|
|<span data-ttu-id="18129-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="18129-503">DATA_TYPE</span></span>|<span data-ttu-id="18129-504">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-504">Int16</span></span>|
|<span data-ttu-id="18129-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-505">TYPE_NAME</span></span>|<span data-ttu-id="18129-506">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-506">String</span></span>|
|<span data-ttu-id="18129-507">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="18129-507">PRECISION</span></span>|<span data-ttu-id="18129-508">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-508">Int32</span></span>|
|<span data-ttu-id="18129-509">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="18129-509">LENGTH</span></span>|<span data-ttu-id="18129-510">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-510">Int32</span></span>|
|<span data-ttu-id="18129-511">ESCALA</span><span class="sxs-lookup"><span data-stu-id="18129-511">SCALE</span></span>|<span data-ttu-id="18129-512">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-512">Int16</span></span>|
|<span data-ttu-id="18129-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="18129-513">RADIX</span></span>|<span data-ttu-id="18129-514">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-514">Int16</span></span>|
|<span data-ttu-id="18129-515">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="18129-515">NULLABLE</span></span>|<span data-ttu-id="18129-516">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-516">Int16</span></span>|
|<span data-ttu-id="18129-517">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="18129-517">REMARKS</span></span>|<span data-ttu-id="18129-518">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-518">String</span></span>|
|<span data-ttu-id="18129-519">SOBRECARGA</span><span class="sxs-lookup"><span data-stu-id="18129-519">OVERLOAD</span></span>|<span data-ttu-id="18129-520">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-520">Int32</span></span>|
|<span data-ttu-id="18129-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="18129-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="18129-522">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-522">Int32</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="18129-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="18129-523">ProcedureParameters</span></span>

|<span data-ttu-id="18129-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="18129-524">ColumnName</span></span>|<span data-ttu-id="18129-525">DataType</span><span class="sxs-lookup"><span data-stu-id="18129-525">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="18129-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="18129-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="18129-527">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-527">String</span></span>|
|<span data-ttu-id="18129-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="18129-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="18129-529">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-529">String</span></span>|
|<span data-ttu-id="18129-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="18129-531">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-531">String</span></span>|
|<span data-ttu-id="18129-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-532">COLUMN_NAME</span></span>|<span data-ttu-id="18129-533">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-533">String</span></span>|
|<span data-ttu-id="18129-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="18129-534">COLUMN_TYPE</span></span>|<span data-ttu-id="18129-535">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-535">Int16</span></span>|
|<span data-ttu-id="18129-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="18129-536">DATA_TYPE</span></span>|<span data-ttu-id="18129-537">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-537">Int16</span></span>|
|<span data-ttu-id="18129-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="18129-538">TYPE_NAME</span></span>|<span data-ttu-id="18129-539">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-539">String</span></span>|
|<span data-ttu-id="18129-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="18129-540">COLUMN_SIZE</span></span>|<span data-ttu-id="18129-541">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-541">Int32</span></span>|
|<span data-ttu-id="18129-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="18129-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="18129-543">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-543">Int32</span></span>|
|<span data-ttu-id="18129-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="18129-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="18129-545">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-545">Int16</span></span>|
|<span data-ttu-id="18129-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="18129-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="18129-547">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-547">Int16</span></span>|
|<span data-ttu-id="18129-548">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="18129-548">NULLABLE</span></span>|<span data-ttu-id="18129-549">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-549">Int16</span></span>|
|<span data-ttu-id="18129-550">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="18129-550">REMARKS</span></span>|<span data-ttu-id="18129-551">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-551">String</span></span>|
|<span data-ttu-id="18129-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="18129-552">COLUMN_DEF</span></span>|<span data-ttu-id="18129-553">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-553">String</span></span>|
|<span data-ttu-id="18129-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="18129-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="18129-555">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-555">Int16</span></span>|
|<span data-ttu-id="18129-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="18129-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="18129-557">Int16</span><span class="sxs-lookup"><span data-stu-id="18129-557">Int16</span></span>|
|<span data-ttu-id="18129-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="18129-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="18129-559">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-559">Int32</span></span>|
|<span data-ttu-id="18129-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="18129-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="18129-561">Int32</span><span class="sxs-lookup"><span data-stu-id="18129-561">Int32</span></span>|
|<span data-ttu-id="18129-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="18129-562">IS_NULLABLE</span></span>|<span data-ttu-id="18129-563">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="18129-563">String</span></span>|

## <a name="see-also"></a><span data-ttu-id="18129-564">Consulte também</span><span class="sxs-lookup"><span data-stu-id="18129-564">See also</span></span>

- <span data-ttu-id="18129-565">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="18129-565">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
