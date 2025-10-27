<!DOCTYPE html>
<html lang="km">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>កម្មវិធីគ្រប់គ្រងចំណូលចំណាយប្រចាំថ្ងៃ</title>
    <!-- ផ្ទុក Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- ផ្ទុក Font Awesome (សម្រាប់ Icons) -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap');
        body {
            font-family: 'Inter', sans-serif;
            background-color: #111827; /* Dark background */
            color: #f3f4f6;
        }
        /* Custom scrollbar for better look in dark mode */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-thumb {
            background-color: #4b5563;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-track {
            background-color: #1f2937;
        }
    </style>
</head>
<body class="min-h-screen p-4 sm:p-8">

    <div id="loading" class="fixed inset-0 bg-gray-900 bg-opacity-75 flex items-center justify-center z-50">
        <div class="flex flex-col items-center">
            <div class="animate-spin rounded-full h-12 w-12 border-b-2 border-indigo-500"></div>
            <p class="mt-4 text-indigo-300">កំពុងផ្ទុកទិន្នន័យ...</p>
        </div>
    </div>

    <header class="text-center mb-10">
        <h1 class="text-3xl sm:text-4xl font-extrabold text-indigo-400">
            <i class="fas fa-wallet mr-2"></i> កម្មវិធីគ្រប់គ្រងហិរញ្ញវត្ថុ
        </h1>
        <p class="text-indigo-300 mt-2">កត់ត្រាចំណូលចំណាយប្រចាំថ្ងៃរបស់អ្នក</p>
    </header>

    <main class="grid grid-cols-1 lg:grid-cols-3 gap-8 max-w-7xl mx-auto">

        <!-- ផ្នែកទី១: បញ្ចូលប្រតិបត្តិការ (Input Form) -->
        <section class="lg:col-span-1 p-6 bg-gray-800 rounded-xl shadow-2xl border border-indigo-700 h-fit">
            <h2 class="text-2xl font-semibold mb-6 text-indigo-400 border-b border-indigo-600 pb-3">
                <i class="fas fa-plus-circle mr-2"></i> បញ្ចូលប្រតិបត្តិការថ្មី
            </h2>
            <form id="transaction-form" class="space-y-4">
                <div>
                    <label for="type" class="block text-sm font-medium mb-1">ប្រភេទប្រតិបត្តិការ:</label>
                    <select id="type" name="type" required
                        class="w-full p-3 border border-gray-600 rounded-lg bg-gray-700 text-white focus:ring-indigo-500 focus:border-indigo-500 transition duration-150">
                        <option value="Income">ចំណូល (Income)</option>
                        <option value="Expense">ចំណាយ (Expense)</option>
                    </select>
                </div>

                <div>
                    <label for="amount" class="block text-sm font-medium mb-1">ចំនួនទឹកប្រាក់ (USD):</label>
                    <input type="number" id="amount" name="amount" required min="0.01" step="0.01"
                        placeholder="ឧ. 15.50"
                        class="w-full p-3 border border-gray-600 rounded-lg bg-gray-700 text-white focus:ring-indigo-500 focus:border-indigo-500 transition duration-150">
                </div>

                <div>
                    <label for="date" class="block text-sm font-medium mb-1">កាលបរិច្ឆេទ:</label>
                    <input type="date" id="date" name="date" required
                        class="w-full p-3 border border-gray-600 rounded-lg bg-gray-700 text-white focus:ring-indigo-500 focus:border-indigo-500 transition duration-150">
                </div>

                <!-- ផ្នែក Category ថ្មីដែលបន្ថែមប៊ូតុងណែនាំ -->
                <div>
                    <label for="description" class="block text-sm font-medium mb-1">បរិយាយ (Description):</label><textarea id="description" name="description" rows="2"
                        placeholder="លម្អិតអំពីប្រតិបត្តិការ"
                        class="w-full p-3 border border-gray-600 rounded-lg bg-gray-700 text-white focus:ring-indigo-500 focus:border-indigo-500 transition duration-150"></textarea>
                </div>

                <div>
                    <div class="flex justify-between items-center mb-1">
                        <label for="category" class="block text-sm font-medium">ប្រភេទ (Category):</label>
                        <button type="button" id="suggest-category-btn"
                            class="text-xs bg-indigo-700 hover:bg-indigo-600 text-white font-medium py-1 px-2 rounded-full transition duration-300 transform hover:scale-105">
                            <i class="fas fa-magic mr-1"></i> ✨ ណែនាំប្រភេទ
                        </button>
                    </div>
                    <input type="text" id="category" name="category" required
                        placeholder="ឧ. ប្រាក់ខែ, ម្ហូបអាហារ, ជួលផ្ទះ"
                        class="w-full p-3 border border-gray-600 rounded-lg bg-gray-700 text-white focus:ring-indigo-500 focus:border-indigo-500 transition duration-150">
                </div>
                
                <button type="submit"
                    class="w-full bg-indigo-600 hover:bg-indigo-700 text-white font-bold py-3 rounded-lg transition duration-300 shadow-md hover:shadow-lg transform hover:scale-[1.01]">
                    <i class="fas fa-save mr-2"></i> រក្សាទុកប្រតិបត្តិការ
                </button>
            </form>
        </section>

        <!-- ផ្នែកទី២: របាយការណ៍ និងទិន្នន័យ -->
        <section class="lg:col-span-2 space-y-8">
            <!-- របាយការណ៍សង្ខេប (Summary Report) -->
            <div class="bg-gray-800 p-6 rounded-xl shadow-2xl border border-indigo-700">
                <h2 class="text-2xl font-semibold mb-4 text-indigo-400">
                    <i class="fas fa-chart-line mr-2"></i> របាយការណ៍សង្ខេបហិរញ្ញវត្ថុ
                </h2>
                <div class="grid grid-cols-1 sm:grid-cols-3 gap-4 text-center">
                    <div class="p-4 rounded-lg bg-green-900 border border-green-700">
                        <p class="text-sm font-medium text-green-300">ចំណូលសរុប (Income)</p>
                        <p id="total-income" class="text-2xl font-bold text-green-400 mt-1">$0.00</p>
                    </div>
                    <div class="p-4 rounded-lg bg-red-900 border border-red-700">
                        <p class="text-sm font-medium text-red-300">ចំណាយសរុប (Expense)</p>
                        <p id="total-expense" class="text-2xl font-bold text-red-400 mt-1">$0.00</p>
                    </div>
                    <div class="p-4 rounded-lg bg-indigo-900 border border-indigo-700">
                        <p class="text-sm font-medium text-indigo-300">សមតុល្យសុទ្ធ (Net Balance)</p>
                        <p id="net-balance" class="text-2xl font-bold text-indigo-400 mt-1">$0.00</p>
                    </div>
                </div>

                <!-- តម្រង (Filter) និង Gemini Analysis -->
                <div class="mt-6 flex flex-col sm:flex-row gap-4 items-center border-t border-gray-700 pt-4">
                    <label for="filter-period" class="text-sm font-medium whitespace-nowrap">តម្រងតាមខែ/ឆ្នាំ:</label>
                    <input type="month" id="filter-period"
                        class="p-2 border border-gray-600 rounded-lg bg-gray-700 text-white focus:ring-indigo-500 focus:border-indigo-500 transition duration-150 w-full sm:w-auto">
                    <button id="clear-filter"
                        class="bg-gray-600 hover:bg-gray-500 text-white py-2 px-4 rounded-lg text-sm transition duration-300 w-full sm:w-auto"><i class="fas fa-times-circle mr-1"></i> លុបតម្រង
                    </button>
                    <button id="analyze-btn"
                        class="bg-fuchsia-600 hover:bg-fuchsia-700 text-white py-2 px-4 rounded-lg text-sm font-bold transition duration-300 w-full sm:w-auto">
                        <i class="fas fa-chart-pie mr-1"></i> ✨ វិភាគហិរញ្ញវត្ថុ
                    </button>
                </div>
                <p id="filter-status" class="text-xs mt-2 text-indigo-300">កំពុងបង្ហាញទិន្នន័យទាំងអស់។</p>

                <!-- លទ្ធផលវិភាគរបស់ Gemini -->
                <div id="analysis-result" class="mt-4 min-h-[50px]">
                    <!-- Analysis result will be displayed here -->
                </div>
            </div>

            <!-- តារាងប្រតិបត្តិការ (Transaction List) -->
            <div class="bg-gray-800 p-6 rounded-xl shadow-2xl border border-indigo-700">
                <h2 class="text-2xl font-semibold mb-4 text-indigo-400">
                    <i class="fas fa-list-alt mr-2"></i> បញ្ជីប្រតិបត្តិការ <span id="list-title-period"></span>
                </h2>
                <!-- ផ្នែកសម្រាប់បង្ហាញបញ្ជី -->
                <div id="transactions-list" class="space-y-3 max-h-[500px] overflow-y-auto">
                    <p class="text-center text-gray-400 p-4" id="no-transactions">
                        <i class="fas fa-info-circle mr-1"></i> មិនទាន់មានប្រតិបត្តិការណាមួយនៅឡើយ។
                    </p>
                </div>
            </div>
        </section>
    </main>

    <!-- Modal សម្រាប់បង្ហាញវិក្កយបត្រ (Invoice/Detail View) -->
    <div id="invoice-modal" class="fixed inset-0 bg-gray-900 bg-opacity-75 hidden items-center justify-center z-50 p-4">
        <div class="bg-gray-800 rounded-xl shadow-3xl max-w-lg w-full p-6 border border-indigo-600">
            <div class="flex justify-between items-center border-b border-indigo-600 pb-3 mb-4">
                <h3 class="text-2xl font-bold text-indigo-400"><i class="fas fa-receipt mr-2"></i> ព័ត៌មានលម្អិត / វិក្កយបត្រ</h3>
                <button id="close-modal" class="text-gray-400 hover:text-white transition duration-200">
                    <i class="fas fa-times text-2xl"></i>
                </button>
            </div>
            <div id="invoice-details" class="space-y-3 text-gray-300">
                <!-- លម្អិតវិក្កយបត្រនឹងត្រូវបញ្ចូលនៅទីនេះ -->
            </div>
            <button id="delete-transaction-btn"
                class="mt-6 w-full bg-red-600 hover:bg-red-700 text-white font-bold py-2 rounded-lg transition duration-300">
                <i class="fas fa-trash-alt mr-2"></i> លុបប្រតិបត្តិការនេះ
            </button>
        </div>
    </div>

    <!-- Firebase & Gemini Imports/Logic -->
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, signInWithCustomToken, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, doc, addDoc, setDoc, deleteDoc, onSnapshot, collection, query, orderBy, where } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

        // Global variables provided by the Canvas environment
        const appId = typeof app_id !== 'undefined' ? app_id : 'default-finance-app-id';
        const firebaseConfig = JSON.parse(typeof firebase_config !== 'undefined' ? firebase_config : '{}');
        const initialAuthToken = typeof initial_auth_token !== 'undefined' ? initial_auth_token : null;

        // Gemini API Configuration
        const API_KEY = ""; 
        const API_URL = "https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-09-2025:generateContent?key=";
        const MAX_RETRIES = 5;

        let db = null;
        let auth = null;
        let userId = null;
        let unsubscribe = null; // សម្រាប់លុបចោល onSnapshot listener