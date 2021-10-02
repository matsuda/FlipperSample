# Uncomment the next line to define a global platform for your project
platform :ios, '10.0'
flipperkit_version = '0.111.0'

target 'FlipperSample' do
  # Comment the next line if you don't want to use dynamic frameworks
  use_frameworks!

  # Pods for FlipperSample

  pod 'Flipper', '~>' + flipperkit_version, :configuration => 'Debug'
  pod 'FlipperKit', '~>' + flipperkit_version, :configuration => 'Debug'
  # pod 'FlipperKit/FlipperKitLayoutComponentKitSupport', '~>' + flipperkit_version, :configuration => 'Debug'
  pod 'FlipperKit/SKIOSNetworkPlugin', '~>' + flipperkit_version, :configuration => 'Debug'
  pod 'FlipperKit/FlipperKitUserDefaultsPlugin', '~>' + flipperkit_version, :configuration => 'Debug'
  # ...unfortunately at this time that means you'll need to explicitly mark
  # transitive dependencies as being for debug build only as well:
  pod 'Flipper-DoubleConversion', :configuration => 'Debug'
  pod 'Flipper-Folly', :configuration => 'Debug'
  pod 'Flipper-Glog', :configuration => 'Debug'
  pod 'Flipper-PeerTalk', :configuration => 'Debug'
  # pod 'CocoaLibEvent', :configuration => 'Debug'
  pod 'OpenSSL-Universal', :configuration => 'Debug'
  pod 'CocoaAsyncSocket', :configuration => 'Debug'
  # pod 'libevent', :configuration => 'Debug'
  # pod 'ComponentKit', '~> 0.31'
end

$static_framework = [
  'Flipper',
  'Flipper-Boost-iOSX', 'Flipper-DoubleConversion', 'Flipper-Fmt', 'Flipper-Folly',
  'Flipper-Glog', 'Flipper-PeerTalk', 'Flipper-RSocket', 'FlipperKit',
  'CocoaAsyncSocket', 'CocoaLibEvent', 'ComponentKit', 'libevent',
  'OpenSSL-Universal', 'SocketRocket', 'boost-for-react-native', 'Yoga', 'YogaKit',
]

pre_install do |installer|
  Pod::Installer::Xcode::TargetValidator.send(:define_method, :verify_no_static_framework_transitive_dependencies) {}
  installer.pod_targets.each do |pod|
    if $static_framework.include?(pod.name)
      def pod.build_type;
        Pod::BuildType.static_library
      end
    end
  end
end
