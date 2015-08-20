'use strict';

angular.module('orfIonic', ['ionic','orf'])

.config(function ($stateProvider, $urlRouterProvider) {
	$stateProvider
	.state('login', {
		url: '/login',
		templateUrl: 'orf-login.html',
		controller: 'UserCtrl'
	})
	.state('signup', {
		url: '/signup',
		templateUrl: 'orf-signup.html',
		controller: 'SignupCtrl'
	})
	.state('pwlogin', {
		url: '/pwlogin',
		templateUrl: 'orf-pwlogin.html',
		controller: 'UserCtrl'
	})
	$urlRouterProvider.otherwise('/login'); 
})

.run(function ($injector, $rootScope) {

	var UserService = $injector.get('UserService');
	var $state = $injector.get('$state');

	// redirect non-authorized routes
	$rootScope.$on('$stateChangeStart', function(event, toState, fromState) {
		if (!UserService.loggedIn() && toState.name !== 'login' && toState.name !== 'signup' && toState.name !== 'pwlogin') {
			$state.go('login');			
			event.preventDefault();
			return;			
		}
	});
})

