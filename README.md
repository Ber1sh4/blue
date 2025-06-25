<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>RentEase - Car & Apartment Rentals</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        .hero {
            background: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url('https://images.unsplash.com/photo-1503376780353-7e6692767b70?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80');
            background-size: cover;
            background-position: center;
        }
        
        .apartment-hero {
            background: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url('https://images.unsplash.com/photo-1560448204-e02f11c3d0e2?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80');
            background-size: cover;
            background-position: center;
        }
        
        .booking-form {
            backdrop-filter: blur(10px);
            background-color: rgba(255, 255, 255, 0.8);
        }
        
        .availability-badge {
            position: absolute;
            top: 10px;
            right: 10px;
            z-index: 10;
        }
        
        .loading-spinner {
            display: none;
            width: 24px;
            height: 24px;
            border: 3px solid rgba(255,255,255,0.3);
            border-radius: 50%;
            border-top-color: #fff;
            animation: spin 1s ease-in-out infinite;
        }
        
        @keyframes spin {
            to { transform: rotate(360deg); }
        }
    </style>
</head>
<body class="font-sans">
    <!-- Navigation -->
    <nav class="bg-white shadow-lg">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between h-16">
                <div class="flex items-center">
                    <div class="flex-shrink-0 flex items-center">
                        <i class="fas fa-car text-blue-600 text-2xl mr-2"></i>
                        <span class="text-xl font-bold text-blue-600">Rent<span class="text-orange-500">Ease</span></span>
                    </div>
                </div>
                <div class="hidden md:flex items-center space-x-8">
                    <a href="#cars" class="text-gray-700 hover:text-blue-600 px-3 py-2 rounded-md text-sm font-medium">Cars</a>
                    <a href="#apartments" class="text-gray-700 hover:text-blue-600 px-3 py-2 rounded-md text-sm font-medium">Apartments</a>
                    <a href="#how-it-works" class="text-gray-700 hover:text-blue-600 px-3 py-2 rounded-md text-sm font-medium">How It Works</a>
                    <a href="#contact" class="text-gray-700 hover:text-blue-600 px-3 py-2 rounded-md text-sm font-medium">Contact</a>
                </div>
                <div class="flex items-center">
                    <button class="bg-blue-600 hover:bg-blue-700 text-white px-4 py-2 rounded-md text-sm font-medium">
                        Sign In
                    </button>
                </div>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <section class="hero text-white py-20">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="md:flex items-center justify-between">
                <div class="md:w-1/2 mb-10 md:mb-0">
                    <h1 class="text-4xl md:text-5xl font-bold mb-4">Find Your Perfect Rental</h1>
                    <p class="text-xl mb-8">Whether you need a car for a weekend getaway or an apartment for your next vacation, we've got you covered.</p>
                    <div class="flex space-x-4">
                        <a href="#cars" class="bg-blue-600 hover:bg-blue-700 text-white px-6 py-3 rounded-md font-medium">Rent a Car</a>
                        <a href="#apartments" class="bg-orange-500 hover:bg-orange-600 text-white px-6 py-3 rounded-md font-medium">Rent an Apartment</a>
                    </div>
                </div>
                <div class="md:w-1/2">
                    <div class="booking-form p-6 rounded-lg shadow-lg max-w-md mx-auto">
                        <h2 class="text-2xl font-bold text-gray-800 mb-4">Check Availability</h2>
                        <div class="mb-4">
                            <label class="block text-gray-700 text-sm font-bold mb-2" for="rental-type">
                                Rental Type
                            </label>
                            <select id="rental-type" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500">
                                <option value="car">Car Rental</option>
                                <option value="apartment">Apartment Rental</option>
                            </select>
                        </div>
                        <div class="mb-4">
                            <label class="block text-gray-700 text-sm font-bold mb-2" for="pickup-location">
                                Location
                            </label>
                            <input type="text" id="pickup-location" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500" placeholder="Enter city or address">
                        </div>
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-4">
                            <div>
                                <label class="block text-gray-700 text-sm font-bold mb-2" for="pickup-date">
                                    Pick-Up Date
                                </label>
                                <input type="date" id="pickup-date" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500">
                            </div>
                            <div>
                                <label class="block text-gray-700 text-sm font-bold mb-2" for="return-date">
                                    Return Date
                                </label>
                                <input type="date" id="return-date" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500">
                            </div>
                        </div>
                        <button id="check-availability" class="w-full bg-blue-600 hover:bg-blue-700 text-white py-2 px-4 rounded-md font-medium flex items-center justify-center">
                            <span id="button-text">Check Availability</span>
                            <div id="loading-spinner" class="loading-spinner ml-2"></div>
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Cars Section -->
    <section id="cars" class="py-16 bg-gray-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-12">
                <h2 class="text-3xl font-bold text-gray-800 mb-2">Our Car Fleet</h2>
                <p class="text-gray-600 max-w-2xl mx-auto">Choose from our wide selection of vehicles for every need and budget</p>
            </div>
            
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                <!-- Car 1 -->
                <div class="bg-white rounded-lg overflow-hidden shadow-md hover:shadow-lg transition-shadow duration-300">
                    <div class="relative">
                        <img src="https://images.unsplash.com/photo-1541899481282-d53b3e40e9c3?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80" alt="Toyota Camry" class="w-full h-48 object-cover">
                        <span class="availability-badge bg-green-500 text-white text-xs font-semibold px-2 py-1 rounded-full">Available</span>
                    </div>
                    <div class="p-6">
                        <div class="flex justify-between items-start mb-2">
                            <h3 class="text-xl font-bold text-gray-800">Toyota Camry</h3>
                            <span class="text-blue-600 font-bold">$45/day</span>
                        </div>
                        <div class="flex items-center text-gray-600 text-sm mb-4">
                            <div class="flex items-center mr-4">
                                <i class="fas fa-users mr-1"></i>
                                <span>5 seats</span>
                            </div>
                            <div class="flex items-center mr-4">
                                <i class="fas fa-gas-pump mr-1"></i>
                                <span>Hybrid</span>
                            </div>
                            <div class="flex items-center">
                                <i class="fas fa-car mr-1"></i>
                                <span>Sedan</span>
                            </div>
                        </div>
                        <p class="text-gray-600 mb-4">Comfortable and fuel-efficient sedan perfect for city driving and road trips.</p>
                        <button class="w-full bg-blue-600 hover:bg-blue-700 text-white py-2 px-4 rounded-md font-medium book-car" data-car-id="1">
                            Book Now
                        </button>
                    </div>
                </div>
                
                <!-- Car 2 -->
                <div class="bg-white rounded-lg overflow-hidden shadow-md hover:shadow-lg transition-shadow duration-300">
                    <div class="relative">
                        <img src="https://images.unsplash.com/photo-1503376780353-7e6692767b70?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80" alt="Jeep Wrangler" class="w-full h-48 object-cover">
                        <span class="availability-badge bg-green-500 text-white text-xs font-semibold px-2 py-1 rounded-full">Available</span>
                    </div>
                    <div class="p-6">
                        <div class="flex justify-between items-start mb-2">
                            <h3 class="text-xl font-bold text-gray-800">Jeep Wrangler</h3>
                            <span class="text-blue-600 font-bold">$75/day</span>
                        </div>
                        <div class="flex items-center text-gray-600 text-sm mb-4">
                            <div class="flex items-center mr-4">
                                <i class="fas fa-users mr-1"></i>
                                <span>4 seats</span>
                            </div>
                            <div class="flex items-center mr-4">
                                <i class="fas fa-gas-pump mr-1"></i>
                                <span>Gasoline</span>
                            </div>
                            <div class="flex items-center">
                                <i class="fas fa-car mr-1"></i>
                                <span>SUV</span>
                            </div>
                        </div>
                        <p class="text-gray-600 mb-4">Iconic off-road vehicle with removable top for adventurous getaways.</p>
                        <button class="w-full bg-blue-600 hover:bg-blue-700 text-white py-2 px-4 rounded-md font-medium book-car" data-car-id="2">
                            Book Now
                        </button>
                    </div>
                </div>
                
                <!-- Car 3 -->
                <div class="bg-white rounded-lg overflow-hidden shadow-md hover:shadow-lg transition-shadow duration-300">
                    <div class="relative">
                        <img src="https://images.unsplash.com/photo-1542362567-b07e54358753?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80" alt="Mercedes-Benz S-Class" class="w-full h-48 object-cover">
                        <span class="availability-badge bg-red-500 text-white text-xs font-semibold px-2 py-1 rounded-full">Booked</span>
                    </div>
                    <div class="p-6">
                        <div class="flex justify-between items-start mb-2">
                            <h3 class="text-xl font-bold text-gray-800">Mercedes S-Class</h3>
                            <span class="text-blue-600 font-bold">$150/day</span>
                        </div>
                        <div class="flex items-center text-gray-600 text-sm mb-4">
                            <div class="flex items-center mr-4">
                                <i class="fas fa-users mr-1"></i>
                                <span>5 seats</span>
                            </div>
                            <div class="flex items-center mr-4">
                                <i class="fas fa-gas-pump mr-1"></i>
                                <span>Gasoline</span>
                            </div>
                            <div class="flex items-center">
                                <i class="fas fa-car mr-1"></i>
                                <span>Luxury</span>
                            </div>
                        </div>
                        <p class="text-gray-600 mb-4">Premium luxury sedan with cutting-edge technology and superior comfort.</p>
                        <button class="w-full bg-gray-400 text-white py-2 px-4 rounded-md font-medium cursor-not-allowed" disabled>
                            Not Available
                        </button>
                    </div>
                </div>
            </div>
            
            <div class="text-center mt-12">
                <a href="#" class="text-blue-600 hover:text-blue-800 font-medium">View All Cars →</a>
            </div>
        </div>
    </section>

    <!-- Apartments Section -->
    <section id="apartments" class="py-16 apartment-hero text-white">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-12">
                <h2 class="text-3xl font-bold mb-2">Featured Apartments</h2>
                <p class="max-w-2xl mx-auto">Comfortable stays for your vacations and business trips</p>
            </div>
            
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                <!-- Apartment 1 -->
                <div class="bg-white rounded-lg overflow-hidden shadow-md hover:shadow-lg transition-shadow duration-300">
                    <div class="relative">
                        <img src="https://images.unsplash.com/photo-1522708323590-d24dbb6b0267?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80" alt="Downtown Loft" class="w-full h-48 object-cover">
                        <span class="availability-badge bg-green-500 text-white text-xs font-semibold px-2 py-1 rounded-full">Available</span>
                    </div>
                    <div class="p-6">
                        <div class="flex justify-between items-start mb-2">
                            <h3 class="text-xl font-bold text-gray-800">Downtown Loft</h3>
                            <span class="text-blue-600 font-bold">$120/night</span>
                        </div>
                        <div class="flex items-center text-gray-600 text-sm mb-4">
                            <div class="flex items-center mr-4">
                                <i class="fas fa-map-marker-alt mr-1"></i>
                                <span>New York</span>
                            </div>
                            <div class="flex items-center mr-4">
                                <i class="fas fa-bed mr-1"></i>
                                <span>2 beds</span>
                            </div>
                            <div class="flex items-center">
                                <i class="fas fa-star mr-1 text-yellow-400"></i>
                                <span>4.8</span>
                            </div>
                        </div>
                        <p class="text-gray-600 mb-4">Modern loft in the heart of downtown with amazing city views and amenities.</p>
                        <button class="w-full bg-blue-600 hover:bg-blue-700 text-white py-2 px-4 rounded-md font-medium book-apartment" data-apartment-id="1">
                            Book Now
                        </button>
                    </div>
                </div>
                
                <!-- Apartment 2 -->
                <div class="bg-white rounded-lg overflow-hidden shadow-md hover:shadow-lg transition-shadow duration-300">
                    <div class="relative">
                        <img src="https://images.unsplash.com/photo-1493809842364-78817add7ffb?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80" alt="Beachfront Villa" class="w-full h-48 object-cover">
                        <span class="availability-badge bg-green-500 text-white text-xs font-semibold px-2 py-1 rounded-full">Available</span>
                    </div>
                    <div class="p-6">
                        <div class="flex justify-between items-start mb-2">
                            <h3 class="text-xl font-bold text-gray-800">Beachfront Villa</h3>
                            <span class="text-blue-600 font-bold">$250/night</span>
                        </div>
                        <div class="flex items-center text-gray-600 text-sm mb-4">
                            <div class="flex items-center mr-4">
                                <i class="fas fa-map-marker-alt mr-1"></i>
                                <span>Miami</span>
                            </div>
                            <div class="flex items-center mr-4">
                                <i class="fas fa-bed mr-1"></i>
                                <span>3 beds</span>
                            </div>
                            <div class="flex items-center">
                                <i class="fas fa-star mr-1 text-yellow-400"></i>
                                <span>4.9</span>
                            </div>
                        </div>
                        <p class="text-gray-600 mb-4">Luxurious beachfront property with private pool and direct beach access.</p>
                        <button class="w-full bg-blue-600 hover:bg-blue-700 text-white py-2 px-4 rounded-md font-medium book-apartment" data-apartment-id="2">
                            Book Now
                        </button>
                    </div>
                </div>
                
                <!-- Apartment 3 -->
                <div class="bg-white rounded-lg overflow-hidden shadow-md hover:shadow-lg transition-shadow duration-300">
                    <div class="relative">
                        <img src="https://images.unsplash.com/photo-1560448204-e02f11c3d0e2?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80" alt="Mountain Cabin" class="w-full h-48 object-cover">
                        <span class="availability-badge bg-red-500 text-white text-xs font-semibold px-2 py-1 rounded-full">Booked</span>
                    </div>
                    <div class="p-6">
                        <div class="flex justify-between items-start mb-2">
                            <h3 class="text-xl font-bold text-gray-800">Mountain Cabin</h3>
                            <span class="text-blue-600 font-bold">$95/night</span>
                        </div>
                        <div class="flex items-center text-gray-600 text-sm mb-4">
                            <div class="flex items-center mr-4">
                                <i class="fas fa-map-marker-alt mr-1"></i>
                                <span>Aspen</span>
                            </div>
                            <div class="flex items-center mr-4">
                                <i class="fas fa-bed mr-1"></i>
                                <span>2 beds</span>
                            </div>
                            <div class="flex items-center">
                                <i class="fas fa-star mr-1 text-yellow-400"></i>
                                <span>4.7</span>
                            </div>
                        </div>
                        <p class="text-gray-600 mb-4">Cozy cabin with fireplace and stunning mountain views, perfect for nature lovers.</p>
                        <button class="w-full bg-gray-400 text-white py-2 px-4 rounded-md font-medium cursor-not-allowed" disabled>
                            Not Available
                        </button>
                    </div>
                </div>
            </div>
            
            <div class="text-center mt-12">
                <a href="#" class="text-white hover:text-gray-300 font-medium">View All Apartments →</a>
            </div>
        </div>
    </section>

    <!-- How It Works Section -->
    <section id="how-it-works" class="py-16 bg-white">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-12">
                <h2 class="text-3xl font-bold text-gray-800 mb-2">How It Works</h2>
                <p class="text-gray-600 max-w-2xl mx-auto">Renting with us is simple and hassle-free</p>
            </div>
            
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <div class="text-center">
                    <div class="bg-blue-100 w-16 h-16 rounded-full flex items-center justify-center mx-auto mb-4">
                        <i class="fas fa-search text-blue-600 text-2xl"></i>
                    </div>
                    <h3 class="text-xl font-semibold text-gray-800 mb-2">1. Search</h3>
                    <p class="text-gray-600">Browse our selection of cars and apartments, filter by your preferences.</p>
                </div>
                
                <div class="text-center">
                    <div class="bg-blue-100 w-16 h-16 rounded-full flex items-center justify-center mx-auto mb-4">
                        <i class="fas fa-calendar-check text-blue-600 text-2xl"></i>
                    </div>
                    <h3 class="text-xl font-semibold text-gray-800 mb-2">2. Book</h3>
                    <p class="text-gray-600">Check availability for your dates and book instantly online.</p>
                </div>
                
                <div class="text-center">
                    <div class="bg-blue-100 w-16 h-16 rounded-full flex items-center justify-center mx-auto mb-4">
                        <i class="fas fa-key text-blue-600 text-2xl"></i>
                    </div>
                    <h3 class="text-xl font-semibold text-gray-800 mb-2">3. Enjoy</h3>
                    <p class="text-gray-600">Pick up your car or check into your apartment and enjoy your rental.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Testimonials Section -->
    <section class="py-16 bg-gray-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-12">
                <h2 class="text-3xl font-bold text-gray-800 mb-2">What Our Customers Say</h2>
                <p class="text-gray-600 max-w-2xl mx-auto">Don't just take our word for it - hear from our satisfied customers</p>
            </div>
            
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <div class="bg-white p-6 rounded-lg shadow-md">
                    <div class="flex items-center mb-4">
                        <div class="flex-shrink-0">
                            <img class="h-10 w-10 rounded-full" src="https://randomuser.me/api/portraits/women/32.jpg" alt="Sarah J.">
                        </div>
                        <div class="ml-3">
                            <h4 class="text-sm font-semibold text-gray-800">Sarah J.</h4>
                            <div class="flex">
                                <i class="fas fa-star text-yellow-400"></i>
                                <i class="fas fa-star text-yellow-400"></i>
                                <i class="fas fa-star text-yellow-400"></i>
                                <i class="fas fa-star text-yellow-400"></i>
                                <i class="fas fa-star text-yellow-400"></i>
                            </div>
                        </div>
                    </div>
                    <p class="text-gray-600">"The apartment was exactly as described - clean, comfortable, and in a great location. Booking was so easy!"</p>
                </div>
                
                <div class="bg-white p-6 rounded-lg shadow-md">
                    <div class="flex items-center mb-4">
                        <div class="flex-shrink-0">
                            <img class="h-10 w-10 rounded-full" src="https://randomuser.me/api/portraits/men/43.jpg" alt="Michael T.">
                        </div>
                        <div class="ml-3">
                            <h4 class="text-sm font-semibold text-gray-800">Michael T.</h4>
                            <div class="flex">
                                <i class="fas fa-star text-yellow-400"></i>
                                <i class="fas fa-star text-yellow-400"></i>
                                <i class="fas fa-star text-yellow-400"></i>
                                <i class="fas fa-star text-yellow-400"></i>
                                <i class="fas fa-star text-yellow-400"></i>
                            </div>
                        </div>
                    </div>
                    <p class="text-gray-600">"Rented a car for our road trip and the process was seamless. The car was in perfect condition and the price was fair."</p>
                </div>
                
                <div class="bg-white p-6 rounded-lg shadow-md">
                    <div class="flex items-center mb-4">
                        <div class="flex-shrink-0">
                            <img class="h-10 w-10 rounded-full" src="https://randomuser.me/api/portraits/women/65.jpg" alt="Emily R.">
                        </div>
                        <div class="ml-3">
                            <h4 class="text-sm font-semibold text-gray-800">Emily R.</h4>
                            <div class="flex">
                                <i class="fas fa-star text-yellow-400"></i>
                                <i class="fas fa-star text-yellow-400"></i>
                                <i class="fas fa-star text-yellow-400"></i>
                                <i class="fas fa-star text-yellow-400"></i>
                                <i class="fas fa-star text-yellow-400"></i>
                            </div>
                        </div>
                    </div>
                    <p class="text-gray-600">"The availability checker was accurate and saved me so much time. Will definitely use RentEase again!"</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="py-16 bg-white">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="lg:grid lg:grid-cols-2 lg:gap-8">
                <div class="mb-8 lg:mb-0">
                    <h2 class="text-3xl font-bold text-gray-800 mb-4">Contact Us</h2>
                    <p class="text-gray-600 mb-6">Have questions or need assistance? Our team is here to help you with your rental needs.</p>
                    
                    <div class="mb-6">
                        <h3 class="text-lg font-semibold text-gray-800 mb-2"><i class="fas fa-phone-alt mr-2 text-blue-600"></i> Phone</h3>
                        <p class="text-gray-600">+1 (555) 123-4567</p>
                    </div>
                    
                    <div class="mb-6">
                        <h3 class="text-lg font-semibold text-gray-800 mb-2"><i class="fas fa-envelope mr-2 text-blue-600"></i> Email</h3>
                        <p class="text-gray-600">support@rentease.com</p>
                    </div>
                    
                    <div>
                        <h3 class="text-lg font-semibold text-gray-800 mb-2"><i class="fas fa-map-marker-alt mr-2 text-blue-600"></i> Address</h3>
                        <p class="text-gray-600">123 Rental Street, Suite 100<br>New York, NY 10001</p>
                    </div>
                </div>
                
                <div class="bg-gray-50 p-6 rounded-lg shadow-md">
                    <h3 class="text-xl font-semibold text-gray-800 mb-4">Send Us a Message</h3>
                    <form>
                        <div class="mb-4">
                            <label class="block text-gray-700 text-sm font-bold mb-2" for="name">
                                Name
                            </label>
                            <input type="text" id="name" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500">
                        </div>
                        <div class="mb-4">
                            <label class="block text-gray-700 text-sm font-bold mb-2" for="email">
                                Email
                            </label>
                            <input type="email" id="email" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500">
                        </div>
                        <div class="mb-4">
                            <label class="block text-gray-700 text-sm font-bold mb-2" for="subject">
                                Subject
                            </label>
                            <select id="subject" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500">
                                <option value="general">General Inquiry</option>
                                <option value="car">Car Rental Question</option>
                                <option value="apartment">Apartment Rental Question</option>
                                <option value="booking">Booking Assistance</option>
                            </select>
                        </div>
                        <div class="mb-4">
                            <label class="block text-gray-700 text-sm font-bold mb-2" for="message">
                                Message
                            </label>
                            <textarea id="message" rows="4" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500"></textarea>
                        </div>
                        <button type="submit" class="w-full bg-blue-600 hover:bg-blue-700 text-white py-2 px-4 rounded-md font-medium">
                            Send Message
                        </button>
                    </form>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="bg-gray-800 text-white py-12">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
                <div>
                    <h3 class="text-lg font-semibold mb-4">RentEase</h3>
                    <p class="text-gray-400">Making car and apartment rentals simple, affordable, and convenient.</p>
                    <div class="flex space-x-4 mt-4">
                        <a href="#" class="text-gray-400 hover:text-white"><i class="fab fa-facebook-f"></i></a>
                        <a href="#" class="text-gray-400 hover:text-white"><i class="fab fa-twitter"></i></a>
                        <a href="#" class="text-gray-400 hover:text-white"><i class="fab fa-instagram"></i></a>
                        <a href="#" class="text-gray-400 hover:text-white"><i class="fab fa-linkedin-in"></i></a>
                    </div>
                </div>
                
                <div>
                    <h3 class="text-lg font-semibold mb-4">Quick Links</h3>
                    <ul class="space-y-2">
                        <li><a href="#" class="text-gray-400 hover:text-white">Home</a></li>
                        <li><a href="#cars" class="text-gray-400 hover:text-white">Cars</a></li>
                        <li><a href="#apartments" class="text-gray-400 hover:text-white">Apartments</a></li>
                        <li><a href="#how-it-works" class="text-gray-400 hover:text-white">How It Works</a></li>
                        <li><a href="#contact" class="text-gray-400 hover:text-white">Contact</a></li>
                    </ul>
                </div>
                
                <div>
                    <h3 class="text-lg font-semibold mb-4">Support</h3>
                    <ul class="space-y-2">
                        <li><a href="#" class="text-gray-400 hover:text-white">FAQs</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white">Privacy Policy</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white">Terms of Service</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white">Cancellation Policy</a></li>
                    </ul>
                </div>
                
                <div>
                    <h3 class="text-lg font-semibold mb-4">Newsletter</h3>
                    <p class="text-gray-400 mb-4">Subscribe to get updates on new listings and special offers.</p>
                    <div class="flex">
                        <input type="email" placeholder="Your email" class="px-3 py-2 bg-gray-700 text-white rounded-l-md focus:outline-none w-full">
                        <button class="bg-blue-600 hover:bg-blue-700 px-4 py-2 rounded-r-md">
                            <i class="fas fa-paper-plane"></i>
                        </button>
                    </div>
                </div>
            </div>
            
            <div class="border-t border-gray-700 mt-8 pt-8 text-center text-gray-400">
                <p>&copy; 2023 RentEase. All rights reserved.</p>
            </div>
        </div>
    </footer>

    <!-- Booking Modal -->
    <div id="booking-modal" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50 hidden">
        <div class="bg-white rounded-lg shadow-xl max-w-md w-full mx-4">
            <div class="p-6">
                <div class="flex justify-between items-center mb-4">
                    <h3 class="text-xl font-bold text-gray-800" id="modal-title">Book Your Rental</h3>
                    <button id="close-modal" class="text-gray-500 hover:text-gray-700">
                        <i class="fas fa-times"></i>
                    </button>
                </div>
                
                <div id="modal-content">
                    <!-- Content will be loaded here -->
                </div>
                
                <div class="mt-6">
                    <button id="confirm-booking" class="w-full bg-blue-600 hover:bg-blue-700 text-white py-2 px-4 rounded-md font-medium">
                        Confirm Booking
                    </button>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Check availability button functionality
        document.getElementById('check-availability').addEventListener('click', function() {
            const button = this;
            const buttonText = document.getElementById('button-text');
            const spinner = document.getElementById('loading-spinner');
            
            // Get form values
            const rentalType = document.getElementById('rental-type').value;
            const location = document.getElementById('pickup-location').value;
            const pickupDate = document.getElementById('pickup-date').value;
            const returnDate = document.getElementById('return-date').value;
            
            // Validate inputs
            if (!location || !pickupDate || !returnDate) {
                alert('Please fill in all fields');
                return;
            }
            
            // Show loading state
            buttonText.textContent = 'Checking...';
            spinner.style.display = 'block';
            button.disabled = true;
            
            // Simulate API call
            setTimeout(function() {
                // Hide loading state
                buttonText.textContent = 'Check Availability';
                spinner.style.display = 'none';
                button.disabled = false;
                
                // Show results (in a real app, this would be dynamic based on API response)
                if (rentalType === 'car') {
                    alert(`Available cars in ${location} from ${pickupDate} to ${returnDate}:\n\n- Toyota Camry\n- Jeep Wrangler\n\nSome vehicles may be unavailable for your selected dates.`);
                } else {
                    alert(`Available apartments in ${location} from ${pickupDate} to ${returnDate}:\n\n- Downtown Loft\n- Beachfront Villa\n\nSome properties may be unavailable for your selected dates.`);
                }
            }, 1500);
        });
        
        // Car booking buttons
        document.querySelectorAll('.book-car').forEach(button => {
            button.addEventListener('click', function() {
                const carId = this.getAttribute('data-car-id');
                openBookingModal('car', carId);
            });
        });
        
        // Apartment booking buttons
        document.querySelectorAll('.book-apartment').forEach(button => {
            button.addEventListener('click', function() {
                const apartmentId = this.getAttribute('data-apartment-id');
                openBookingModal('apartment', apartmentId);
            });
        });
        
        // Open booking modal
        function openBookingModal(type, id) {
            const modal = document.getElementById('booking-modal');
            const modalTitle = document.getElementById('modal-title');
            const modalContent = document.getElementById('modal-content');
            
            // Set title based on type
            modalTitle.textContent = type === 'car' ? 'Book Your Car' : 'Book Your Apartment';
            
            // Load appropriate content
            if (type === 'car') {
                modalContent.innerHTML = `
                    <div class="mb-4">
                        <label class="block text-gray-700 text-sm font-bold mb-2" for="car-pickup-date">
                            Pick-Up Date
                        </label>
                        <input type="date" id="car-pickup-date" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500">
                    </div>
                    <div class="mb-4">
                        <label class="block text-gray-700 text-sm font-bold mb-2" for="car-return-date">
                            Return Date
                        </label>
                        <input type="date" id="car-return-date" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500">
                    </div>
                    <div class="mb-4">
                        <label class="block text-gray-700 text-sm font-bold mb-2" for="car-pickup-location">
                            Pick-Up Location
                        </label>
                        <input type="text" id="car-pickup-location" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500" placeholder="Enter pickup location">
                    </div>
                `;
            } else {
                modalContent.innerHTML = `
                    <div class="mb-4">
                        <label class="block text-gray-700 text-sm font-bold mb-2" for="apartment-checkin">
                            Check-In Date
                        </label>
                        <input type="date" id="apartment-checkin" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500">
                    </div>
                    <div class="mb-4">
                        <label class="block text-gray-700 text-sm font-bold mb-2" for="apartment-checkout">
                            Check-Out Date
                        </label>
                        <input type="date" id="apartment-checkout" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500">
                    </div>
                    <div class="mb-4">
                        <label class="block text-gray-700 text-sm font-bold mb-2" for="apartment-guests">
                            Number of Guests
                        </label>
                        <input type="number" id="apartment-guests" min="1" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500" placeholder="Enter number of guests">
                    </div>
                `;
            }
            
            // Show modal
            modal.classList.remove('hidden');
        }
        
        // Close modal
        document.getElementById('close-modal').addEventListener('click', function() {
            document.getElementById('booking-modal').classList.add('hidden');
        });
        
        // Confirm booking
        document.getElementById('confirm-booking').addEventListener('click', function() {
            alert('Booking confirmed! You will receive a confirmation email shortly.');
            document.getElementById('booking-modal').classList.add('hidden');
        });
        
        // Close modal when clicking outside
        document.getElementById('booking-modal').addEventListener('click', function(e) {
            if (e.target === this) {
                this.classList.add('hidden');
            }
        });
    </script>
</body>
</html>
