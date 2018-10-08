# Processing-Python-School-Data
{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Keiana Python Mini Project   \n",
    "Loading file: Working with lists; Enumerating; Sequencing thru multiple lists at once with zip\n",
    "List comprehension, String functions; Set datastructure; Value in testing data processing code\n",
    "Dictionaries; Converting strings to floats; Built-in Python aggregated functions; Dynamically appending to lists"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Locate data on my computer"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "ls "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "ls Documents/"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Load data into Python"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "!locate 'userssharedsdfschoolimprovement2010grants.csv'"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "from IPython.core.display import display, HTML\n",
    "display(HTML(\"<style>.container { width:100% !important; }</style>\"))"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "with open('/home/ktd2001/Documents/DSSA_5102_Data_Gathering_and_Warehousing/userssharedsdfschoolimprovement2010grants.csv', 'r') as f:\n",
    "    data = f.readlines()   # \"r\" used to read the file"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Taking a look at the list of records"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "type(data)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "data[0:10]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "(len(data) -1) / 3"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "columns = data[0]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "columns"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Isolating the records since each covers 3 rows"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "data[1:22]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "data [1:22:3]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "len(data[1:22:3])"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "data[2:22:3]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "len(data[2:22:3])"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "data[3:22:3]"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Combining 3 list (Zip function) used to concatenate data to isolate records"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "for part_1, part_2, part_3 in zip(data[1:22:3], data[2:22:3], data[3:22:3]):\n",
    "    record = (part_1 + part_2 + part_3)\n",
    "    record = record.replace(\"\\n\", \"\")\n",
    "    print(record)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "records = []\n",
    "\n",
    "for part_1, part_2, part_3 in zip(data[1:22:3], data[2:22:3], data[3:22:3]):\n",
    "    record = (part_1 + part_2 + part_3)\n",
    "    record = record.replace(\"\\n\", \"\")\n",
    "    records.append(record)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "len(records)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Go through whole record list, looped them and removed newline characters to reach records shows up on own line"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "records = []\n",
    "\n",
    "for part_1, part_2, part_3 in zip(data[1::3], data[2::3], data[3::3]):\n",
    "    record = (part_1 + part_2 + part_3)\n",
    "    record = record.replace(\"\\n\", \"\")\n",
    "    records.append(record)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "len(records)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "records[0:10]"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "List comprehension technique"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "records = [ (x+y+z).replace('\\n', \"\") for x,y,z in zip(data[1::3], data[2::3], data[3::3]) ]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "len(records)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "for record in records[0:10]:\n",
    "     print(records)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "columns.strip().split(\",\")  #To remove commmas and replace with spaces"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "Using a set to help guide testing"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "number_of_fields = set()\n",
    "\n",
    "for record in records:\n",
    "    number_of_fields.add(\n",
    "        len( record.split(\",\") )\n",
    "    )\n",
    "number_of_fields"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "records[0]"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Testing revealed structure was not right"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "records[0].split(\",\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "number_of_fields = set()\n",
    "for record in records:\n",
    "    if  \"PHILADELPHIA CITY SD\" in record:\n",
    "        number_of_fields.add(len(record.split(\",\")))\n",
    "number_of_fields"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Dictionary"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "dataset = {\n",
    "    \"SCHOOL_NAME\": [\"school\"],  \n",
    "    \"AMOUNT\":      [123],\n",
    "    \"MODEL\":       [\"model_val\"]\n",
    "}"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "dataset"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "dataset[\"MODEL\"]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "columns"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "some_value = \"$737032.00\" "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "float(some_value[1:] )"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "dataset = {\n",
    "    \"SCHOOL_NAME\": [],\n",
    "    \"AMOUNT\": [],\n",
    "    \"MODEL\": [],\n",
    "}\n",
    "\n",
    "for record in records:\n",
    "    if \"PHILADELPHIA CITY SD\" in record:\n",
    "        fields = record.split(\",\")\n",
    "        \n",
    "        school_name = fields[0]\n",
    "        amount = float(fields[4][1:]) #Technique of slicing to remove $ so number can appear as an amount\n",
    "        model = fields [5]\n",
    "        \n",
    "        dataset[\"SCHOOL_NAME\"].append(school_name)\n",
    "        dataset[\"AMOUNT\"].append(amount)\n",
    "        dataset[\"MODEL\"].append(model)\n",
    "        \n",
    "dataset"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "dataset[\"AMOUNT\"]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "sum( dataset[\"AMOUNT\"] )"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.6.5"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 2
}
